

<script type="text/javascript" src="{{site.data.info.assets}}assets/js/jquery.js"> </script>
<script type="text/javascript" src="{{site.data.info.assets}}assets/js/jquery-ui.min.js"> </script>
{% if includetabscripts %}
  <script type="text/javascript" src="{{site.data.info.assets}}assets/js/tabs.js"> </script>
{% endif %}
<script type="text/javascript" src="{{site.data.info.assets}}assets/js/window-hash.js"> </script>

<!-- <div style="height: 4rem;"> </div> -->
<div id="segment-footer" igtool="footer" class="segment"><!-- segment-footer -->
<div class="container"><!-- container -->
{% if shownav == 'y' %}
<div style="background-color:var(--footer-nav-bg-color)">
  <table style="width:100%">
    <tbody>
      <tr>
        <td style="text-align:left">&#xA0;
{% if site.data.pages[page.path].previous %}
          <a href="{{site.data.pages[page.path].previous}}">&lt;prev</a>
{% else %}
          <span style="visibility:hidden">&lt;prev</span>
{% endif %}
        </td>
        <td style="text-align:center">
          <a href="#top">top</a>
        </td>
        <td style="text-align:right">&#xA0;
{% if site.data.pages[page.path].next %}
          <a href="{{site.data.pages[page.path].next}}">next&gt;</a>
{% else %}
          <span style="visibility:hidden">next&gt;</span>
{% endif %}
        </td>
      </tr>
    </tbody>
  </table>
</div>
{% endif %}
<div class="inner-wrapper">
  <p>
    IG &#169; {{site.data.info.copyrightyear}} <a style="color:var(--footer-hyperlink-text-color)" href="{{site.data.fhir.ig.contact[0].telecom[0]}}">{{site.data.fhir.ig.publisher | escape}}</a>.  Package {{site.data.fhir.packageId}}#{{site.data.fhir.igVer}} based on <a style="color: var(--footer-hyperlink-text-color)" href="{{site.data.fhir.path}}">FHIR® {{site.data.fhir.version}}</a>. Generated <span title="{{site.data.fhir.genDate}}">{{site.data.fhir.genDate | date: "%Y-%m-%d"}}</span>
    <br/>
    <span>
      {% include fragment-footer.html %}
    </span>
  </p>
</div><!-- /inner-wrapper -->
</div><!-- /container -->
</div><!-- /segment-footer -->
<div id="segment-post-footer" class="segment hidden"><!-- segment-post-footer -->
<div class="container"><!-- container -->
</div><!-- /container -->
</div><!-- /segment-post-footer -->


</div>