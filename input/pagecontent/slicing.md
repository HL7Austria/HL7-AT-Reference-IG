<div class="dragon" markdown="1">
The following applies to elements other than `code` (in this case we focused on `Composition.section.code`) as long as they are of type CodeableConcept e.g. `Composition.type`
</div>

### tl;dr - IF YOU DO NOT WANT TO READ THE WHOLE PAGE

**Do not use `exactly` in general!** `exactly` leads to considerable restrictions (see below).

If **at least 1 Coding** with the specified values should occur in the slice:
- `discriminator.path = "code"` (=CodeableConcept level)

If **exactly 1 Coding** with the specified values should occur in the slice and no other Coding:
- `discriminator.path = "code.coding"` or `discriminator.path = "code.coding.code"` (=Coding or Code level)
- There is no difference between the two if `exactly` is not used.

### Basic rules

#### Relationship between discriminator.path and slice level

**`discriminator.path` and the level at which the individual slices are specified must match!** See the following example.

<style>
.my-table {
  width: 100%;
  table-layout: fixed;
}

.my-table .img-cell {
  max-width: 100%;
  height: auto;
  display: block;
}

.my-table, .my-table th, .my-table td {
  border: 1px solid black;
}

.correct pre {
  background-color: #90EE90;
}
.correct .highlight {
  background-color: #4E9A4E;
}

.wrong pre {
  background-color: #FFB6B6;
}
.wrong .highlight {
  background-color: #B84A4A;
}
</style>

<table class="my-table">
  <tr>
    <th>Correct</th>
    <th>Wrong</th>
  </tr>
  <tr>
    <td>Use of <code>code</code> in <code>discriminator.path</code> and setting the code on <code>section.code</code>.</td>
    <td>Use of <code>code.coding.code</code> in <code>discriminator.path</code> and setting the code on <code>section.code</code>.</td>
  </tr>
  <tr>
    <td class="correct"><pre>
* section.code from ExampleCompositionSectionsVS
* section ^slicing.discriminator[+].type = #value
* section ^slicing.discriminator[=].path = <span class="highlight">"code"</span>
* section ^slicing.rules = #open
* section contains Section1 1..
* section[Section1].<span class="highlight">code</span> = ExampleCompositionSectionsCS#Section1
* section contains Section2 1..
* section[Section2].<span class="highlight">code</span> = ExampleCompositionSectionsCS#Section2
* section contains Section3 1..
* section[Section3].<span class="highlight">code</span> = ExampleCompositionSectionsCS#Section3
    </pre></td>
    <td class="wrong"><pre>
* section.code from ExampleCompositionSectionsVS
* section ^slicing.discriminator[+].type = #value
* section ^slicing.discriminator[=].path = <span class="highlight">"code.coding.code"</span>
* section ^slicing.rules = #open
* section contains Section1 1..
* section[Section1].<span class="highlight">code</span> = ExampleCompositionSectionsCS#Section1
* section contains Section2 1..
* section[Section2].<span class="highlight">code</span> = ExampleCompositionSectionsCS#Section2
* section contains Section3 1..
* section[Section3].<span class="highlight">code</span> = ExampleCompositionSectionsCS#Section3
    </pre></td>
  </tr>
</table>

#### Consistent slice level

**All slices must use the same slice level!** See the following example:

<table class="my-table">
  <tr>
    <th>Correct</th>
    <th>Wrong</th>
  </tr>
  <tr>
    <td>Use of <code>code</code> in <code>discriminator.path</code> and setting the code on <code>section.code</code>.</td>
    <td>Use of <code>code</code> in <code>discriminator.path</code> and setting the code on <code>section.code.coding</code> for <code>Section2</code></td>
  </tr>
  <tr>
    <td class="correct"><pre>
* section.code from ExampleCompositionSectionsVS
* section ^slicing.discriminator[+].type = #value
* section ^slicing.discriminator[=].path = <span class="highlight">"code"</span>
* section ^slicing.rules = #open
* section contains Section1 1..
* section[Section1].<span class="highlight">code</span> = ExampleCompositionSectionsCS#Section1
* section contains Section2 1..
* section[Section2].<span class="highlight">code</span> = ExampleCompositionSectionsCS#Section2
* section contains Section3 1..
* section[Section3].<span class="highlight">code</span> = ExampleCompositionSectionsCS#Section3
    </pre></td>
    <td class="wrong"><pre>
* section.code from ExampleCompositionSectionsVS
* section ^slicing.discriminator[+].type = #value
* section ^slicing.discriminator[=].path = <span class="highlight">"code"</span>
* section ^slicing.rules = #open
* section contains Section1 1..
* section[Section1].<span class="highlight">code</span> = ExampleCompositionSectionsCS#Section1
* section contains Section2 1..
* section[Section2].<span class="highlight">code.coding</span> = ExampleCompositionSectionsCS#Section2
    </pre></td>
  </tr>
</table>

### Effects of different discriminator.path settings (WITHOUT exactly)

#### discriminator.path = "code" (CodeableConcept level) (WITHOUT exactly)

<table class="my-table">
  <tr>
    <th>FSH</th>
    <th>IG</th>
  </tr>
  <tr>
    <td colspan="2"><a href="StructureDefinition-ExampleComposition4.html">ExampleComposition4</a></td>
  </tr>
  <tr>
    <td><pre>
* section.code from ExampleCompositionSectionsVS
* section ^slicing.discriminator[+].type = #value
* section ^slicing.discriminator[=].path = "code"
* section ^slicing.rules = #open
* section contains Section2 1..
* section[Section2].code = ExampleCompositionSectionsCS#Section2
    </pre></td>
    <td><img src="CodeableConcept-level-slicing.png" class="img-cell"></td>
  </tr>
</table>

#### discriminator.path = "code.coding" (Coding level) (WITHOUT exactly)

<table class="my-table">
  <tr>
    <th>FSH</th>
    <th>IG</th>
  </tr>
  <tr>
    <td colspan="2"><a href="StructureDefinition-ExampleComposition5.html">ExampleComposition5</a></td>
  </tr>
  <tr>
    <td><pre>
* section.code from ExampleCompositionSectionsVS
* section ^slicing.discriminator[+].type = #value
* section ^slicing.discriminator[=].path = "code.coding"
* section ^slicing.rules = #open
* section contains Section2 1..
* section[Section2].code.coding = ExampleCompositionSectionsCS#Section2
    </pre></td>
    <td><img src="Coding-level-slicing.png" class="img-cell"></td>
  </tr>
</table>

#### discriminator.path = "code.coding.code" (Code level) (WITHOUT exactly)

<table class="my-table">
  <tr>
    <th>FSH</th>
    <th>IG</th>
  </tr>
  <tr>
    <td colspan="2"><a href="StructureDefinition-ExampleComposition6.html">ExampleComposition6</a></td>
  </tr>
  <tr>
    <td><pre>
* section.code from ExampleCompositionSectionsVS
* section ^slicing.discriminator[+].type = #value
* section ^slicing.discriminator[=].path = "code.coding.code"
* section ^slicing.rules = #open
* section contains Section2 1..
* section[Section2].code.coding.system = Canonical(ExampleCompositionSectionsCS)
* section[Section2].code.coding.code = #Section2
    </pre></td>
    <td><img src="Code-level-slicing.png" class="img-cell"></td>
  </tr>
</table>

### Effects of different discriminator.path settings (WITH exactly)

#### discriminator.path = "code" (CodeableConcept level) (WITH exactly)

<table class="my-table">
  <tr>
    <th>FSH</th>
    <th>IG</th>
  </tr>
  <tr>
    <td colspan="2"><a href="StructureDefinition-ExampleComposition4.html">ExampleComposition4</a></td>
  </tr>
  <tr>
    <td><pre>
* section.code from ExampleCompositionSectionsVS
* section ^slicing.discriminator[+].type = #value
* section ^slicing.discriminator[=].path = "code"
* section ^slicing.rules = #open
* section contains Section1 1..
* section[Section1].code = ExampleCompositionSectionsCS#Section1 (exactly)
    </pre></td>
    <td><img src="CodeableConcept-level-slicing_exactly.png" class="img-cell"></td>
  </tr>
</table>

#### discriminator.path = "code.coding" (Coding level) (WITH exactly)

<table class="my-table">
  <tr>
    <th>FSH</th>
    <th>IG</th>
  </tr>
  <tr>
    <td colspan="2"><a href="StructureDefinition-ExampleComposition5.html">ExampleComposition5</a></td>
  </tr>
  <tr>
    <td><pre>
* section.code from ExampleCompositionSectionsVS
* section ^slicing.discriminator[+].type = #value
* section ^slicing.discriminator[=].path = "code.coding"
* section ^slicing.rules = #open
* section contains Section1 1..
* section[Section1].code.coding = ExampleCompositionSectionsCS#Section1 (exactly)
    </pre></td>
    <td><img src="Coding-level-slicing_exactly.png" class="img-cell"></td>
  </tr>
</table>

#### discriminator.path = "code.coding.code" (Code level) (WITH exactly)

<table class="my-table">
  <tr>
    <th>FSH</th>
    <th>IG</th>
  </tr>
  <tr>
    <td colspan="2"><a href="StructureDefinition-ExampleComposition6.html">ExampleComposition6</a></td>
  </tr>
  <tr>
    <td><pre>
* section.code from ExampleCompositionSectionsVS
* section ^slicing.discriminator[+].type = #value
* section ^slicing.discriminator[=].path = "code.coding.code"
* section ^slicing.rules = #open
* section contains Section1 1..
* section[Section1].code.coding.system = Canonical(ExampleCompositionSectionsCS)
* section[Section1].code.coding.code = #Section1 (exactly)
    </pre></td>
    <td><img src="Code-level-slicing_exactly.png" class="img-cell"></td>
  </tr>
</table>

### Required Pattern vs. Fixed Value

#### Rendering in the IG vs. StructureDefinition

The IG Publisher adapts the rendering to the hierarchy (see [Effects of different discriminator.path settings (WITHOUT exactly)](#effects-of-different-discriminatorpath-settings-without-exactly)). The highest hierarchy level is always decisive for the assessment of a slice. This means that if `discriminator.path = "code"` is specified, the relevant information as to whether it is a pattern ([ElementDefinition pattern\[x\]](https://build.fhir.org/elementdefinition-definitions.html#ElementDefinition.pattern_x_)) or a fixed value ([ElementDefinition fixed\[x\]](https://build.fhir.org/elementdefinition-definitions.html#ElementDefinition.fixed_x_)) is found at the CodeableConcept level. In the hierarchies below, the IG Publisher still states "Fixed value", even if it may only be a pattern in terms of the StructureDefinition.

#### Setting fixed values in FSH

Only specifying `exactly` in FSH results in a fixed value in the StructureDefinition. Everything else results in a pattern in the StructureDefinition.

<table class="my-table">
  <tr>
    <th></th>
    <th>WITHOUT <code>exactly</code></th>
    <th>WITH <code>exactly</code></th>
  </tr>
  <tr>
    <td><strong>CodeableConcept level</strong></td>
    <td>If a pattern is set at the CodeableConcept level, additional codings are allowed.</td>
    <td>If a fixed value is set at the CodeableConcept level, no additional codings are allowed. Furthermore, populating elements other than those defined by the slice is forbidden.</td>
  </tr>
  <tr>
    <td><strong>Coding level</strong></td>
    <td>If a pattern is set at the Coding level, in addition to the specified code, displays, extensions, etc. can also be used.</td>
    <td>If a fixed value is set at the Coding level, only the specified elements with the fixed values may occur underneath, and no other elements, e.g. if system, code and display are fixed, then these must be present and match the specified values, and e.g. a version or extension is not allowed.</td>
  </tr>
  <tr>
    <td><strong>Code level</strong></td>
    <td colspan="2">Pattern and fixed value mean the same thing for primitive data types (system -> uri, code -> code) - i.e. an exact match is required.</td>
  </tr>
</table>

### Recommendations

#### Allowing additional codings

If additional code+system combinations should be allowed, then `discriminator.path = "code"` (CodeableConcept level) must be used.
Whether additional fields are allowed in the coding defined by the slice (display, extension, ...) depends on whether `exactly` is used on `code` (CodeableConcept level) or not. When using `exactly` on `code` (CodeableConcept level), no other elements are allowed.

#### Only one code + system combination allowed and no other

If no additional code+system combinations should be allowed, then `discriminator.path = "code.coding"` or `discriminator.path = "code.coding.code"` must be used.
Whether additional fields are allowed in the coding defined by the slice (display, extension, ...) depends on whether `exactly` is used on `code.coding` or not. When using `exactly` on `code.coding` (Coding level), no other elements are allowed.

