{% include general-header.md %}

<div class="segment" id="segment-navbar">
  <div id="stripe"></div>
  <div class="container">
    <nav class="navbar navbar-inverse">
      <div class="container">
        <div class="nav-collapse collapse navbar-inverse-collapse">
          <ul class="nav navbar-nav">
            <li><a href="base.html">Home</a></li>
            <li><a href="base-toc.html">Table of Contents</a></li>
            <li><a href="base-artifacts.html">Artifacts</a></li>
             <li class="dropdown">
              <a href="#" class="dropdown-toggle" data-toggle="dropdown">About <b class="caret"></b></a>
              <ul class="dropdown-menu">
                <li><a href="base-authors.html">Authors and Contributors</a></li>
                <li><a href="base-downloads.html">Download</a></li>
                <li><a href="base-dependencies.html">Dependencies</a></li>
                <li><a href="base-copyright.html">Copyright</a></li>
                <li><a href="base-cross-version-analysis.html">Cross-Version Analysis</a></li>
                <li><a href="base-known-issues.html">Known Issues</a></li>
                <li><a target="_blank" href="{{site.data.fhir.path}}index.html">FHIR® Spec</a></li>
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