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
          <table class="table-minimal">
            <thead>
              <tr>
                <th>Day</th>
                <th>Start Time</th>
                <th>Tests</th>
              </tr>
            </thead>
            <tbody>
              {% for day in days %}
                {% for data in day %}
                  <tr>
                    <td>{{data.date | date: "%A %d, %Y"}}</td>
                    <td>{{data.date | date: "%l:%M%P"}}</td>
                    <td>
                      <ul>
                        {% for test in tests %}
                          <li>{{test}}</li>
                        {% endfor %}
                      </ul>
                    </td>
                  </tr>
                {% endfor %}
              {% endfor %}
            </tbody>
          </table>
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
          {% for forms in test.forms %}
            {% for form in forms %}
              <a href="{{form.file}}" target="blank">{{form.label}}</a><br>
            {% endfor %}
          {% endfor %}
        </div>
      </div>
    </div>
  </div>
{% endfor %}
<script src="/javascript/vertical_tabs.js"></script>
