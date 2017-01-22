---
title: Testing
date: 2017-01-15 13:23:00 -08:00
menu_name: Testing
layout: page
---

{% for test in site.tests %}
  <div class="row row-1">
    <h2>{{test.title}}</h2>
    <div class="vertical-tabs-container">
      <div class="vertical-tabs">
        <a href="javascript:void(0)" class="js-vertical-tab vertical-tab is-active" rel="tab1">Dates & Times</a>
        <a href="javascript:void(0)" class="js-vertical-tab vertical-tab" rel="tab2">Location</a>
        <a href="javascript:void(0)" class="js-vertical-tab vertical-tab" rel="tab3">Entry Fees</a>
        <a href="javascript:void(0)" class="js-vertical-tab vertical-tab" rel="tab4">Forms</a>
      </div>

      <div class="vertical-tab-content-container">
        <a href="" class="js-vertical-tab-accordion-heading vertical-tab-accordion-heading is-active" rel="tab1">Dates & Times</a>
        <div id="tab1" class="js-vertical-tab-content vertical-tab-content">
          {{test.start_date | date: "%A, %B %d, %Y"}}<br>
          {{test.end_date | date: "%A, %B %d, %Y"}}
        </div>

        <a href="" class="js-vertical-tab-accordion-heading vertical-tab-accordion-heading" rel="tab2">Location</a>
        <div id="tab2" class="js-vertical-tab-content vertical-tab-content">
          {{test.location.city}}, {{test.location.state}}
        </div>

        <a href="" class="js-vertical-tab-accordion-heading vertical-tab-accordion-heading" rel="tab3">Entry Fees</a>
        <div id="tab3" class="js-vertical-tab-content vertical-tab-content">
          {% for info in test.tests %}
            {% for data in info %}
              {% if data.is_scheduled %}
                {{data.name}}<br>
              {% endif %}
            {% endfor %}
          {% endfor %}
        </div>

        <a href="" class="js-vertical-tab-accordion-heading vertical-tab-accordion-heading" rel="tab4">Forms</a>
        <div id="tab4" class="js-vertical-tab-content vertical-tab-content">
          <p>Sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Phasellus dui urna, mollis vel suscipit in, pharetra at ligula. Pellentesque a est vel est fermentum pellentesque sed sit amet dolor. Nunc in dapibus nibh. Aliquam erat volutpat. Phasellus vel dui sed nibh iaculis convallis id sit amet urna. Proin nec tellus quis justo consequat accumsan. Vivamus turpis enim, auctor eget placerat eget, aliquam ut sapien.</p>
        </div>
      </div>
    </div>
  </div>
{% endfor %}
<script src="/javascript/vertical_tabs.js"></script>
