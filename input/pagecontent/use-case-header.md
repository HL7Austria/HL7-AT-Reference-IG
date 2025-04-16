{% include general-header.md %}

<div class="segment" id="segment-navbar">
  <div id="stripe"></div>
  <div class="container">
    <nav class="navbar navbar-inverse">
      <div class="container">
        <div class="nav-collapse collapse navbar-inverse-collapse">
          <ul class="nav navbar-nav">
            <li><a href="use-case.html">Home</a></li>
            <li><a href="use-case-toc.html">Table of Contents</a></li>
            <li><a href="use-case-artifacts.html">Artifacts</a></li>
            <li><a href="use-case-background.html">Background</a></li>
            <li class="dropdown">
              <a href="#" class="dropdown-toggle" data-toggle="dropdown">[Optional] <b class="caret"></b></a>
              <ul class="dropdown-menu">
                <li><a href="use-case-use-cases.html">[Use Cases]</a></li>
                <li><a href="use-case-workflow.html">[Workflow]</a></li>
                <li><a href="use-case-actors.html">[Actors]</a></li>
                <li><a href="use-case-mapping.html">[Mapping]</a></li>
                <li><a href="use-case-terminologies.html">[Terminologies]</a></li>
                <li><a href="use-case-technical-information.html">[Technical Information]</a></li>
                <li><a href="use-case-model.html">[Model]</a></li>
                <li><a href="use-case-examples.html">[Examples]</a></li>
              </ul>
            </li>
             <li class="dropdown">
              <a href="#" class="dropdown-toggle" data-toggle="dropdown">Other <b class="caret"></b></a>
              <ul class="dropdown-menu">
                <li><a href="use-case-about.html">About</a></li>
                <li><a href="use-case-downloads.html">Downloads</a></li>
                <li class="divider"></li>
                <li>
                  <a target="_blank" href="{{site.data.fhir.path}}index.html">
                    FHIR® Spec
                  </a>
                </li>
              </ul>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </div>
</div>

<style>
  .no-number {
    --heading-prefix: none;
  }
</style>