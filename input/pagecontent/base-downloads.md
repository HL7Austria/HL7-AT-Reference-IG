{% include base-header.md %}

<h2 class="no-number">Downloads</h2>

Resources and downloadable materials for the Base IG.

This section could look like this:

<h3 class="no-number">Full IG</h3>

Download the entire implementation guide [here](full-ig.zip).

<h3 class="no-number">NPM Package and Definitions</h3>

The following file contains all the value sets, profiles, extensions, list of pages and urls in the IG, etc. defined as part of this Implementation Guide:

- [NPM Package](package.tgz)

In addition there are format specific definition files:

- [XML](definitions.xml.zip)
- [JSON](definitions.json.zip)
- [TTL](definitions.ttl.zip)

These files should be the first choice whenever generating any implementation artifacts since they contain all of the rules about what makes these profiles valid. Implementers will still need to be familiar with the content of the specification and profiles that apply in order to make a conformant implementation.  See the overview on [validating FHIR profiles and resources]({{ site.data.fhir.path }}validation.html).

<h3 class="no-number">Examples</h3>

All of the examples that are used in this Implementation Guide are available for download:

- [XML](examples.xml.zip)
- [JSON](examples.json.zip)

{% include general-footer.md %}