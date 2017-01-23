---
title: Testing
date: 2017-01-15 13:23:00 -08:00
menu_name: Testing
header_image: "/uploads/navhda-test-2.jpg"
page_header_title: CONAVHDA Tests
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
          <table class="table-minimal">
            <thead>
              <tr>
                <th>Day</th>
                <th>Start Time</th>
                <th>Tests</th>
              </tr>
            </thead>
            <tbody>
              {% for day in test.days %}
                <tr>
                  {% for data in day %}
                    <!-- some sort of glitch that I have to work around -->
                    {% if data.size < 5 %}
                      <td>{{data.date | date: "%A, %B %d, %Y"}}</td>
                      <td>{{data.date | date: "%l:%M%P"}}</td>
                      <td>
                        <ul>
                          {% for test in data.tests %}
                            <li>{{test}}</li>
                          {% endfor %}
                        </ul>
                      </td>
                    {% endif %}
                  {% endfor %}
                </tr>
            {% endfor %}
            </tbody>
          </table>
        </div>

        <a href="" class="js-vertical-tab-accordion-heading vertical-tab-accordion-heading" rel="tab2">Location</a>
        <div id="tab2" class="js-vertical-tab-content vertical-tab-content">
          <h3>{{test.location.city}}, {{test.location.state}}</h3>
          <p>Location: {{test.location.address_or_landmark}}</p>
          <p>Latitude and Longitude: {{test.location.latitude}}, {{test.location.longitude}}</p>
          <div class="cards">
            <div class="card">
              <div class="card-image">
                <img src="https://raw.githubusercontent.com/thoughtbot/refills/master/source/images/mountains.png" alt="">
              </div>
              <div class="card-header">
                Directions
              </div>
              <div class="card-copy">
                <p>{{test.location.directions}}</p>
              </div>
            </div>

          </div>
        </div>

        <a href="" class="js-vertical-tab-accordion-heading vertical-tab-accordion-heading" rel="tab3">Entry Fees</a>
        <div id="tab3" class="js-vertical-tab-content vertical-tab-content">
          <table class="table-minimal">
            <thead>
              <tr>
                <th>Test</th>
                <th>Member Price</th>
                <th>Non-Member Price</th>
              </tr>
            </thead>
            <tbody>
              {% for data in test.tests %}
                <tr>
                  {% for info in data %}
                    {% if info.is_scheduled %}
                      <td>{{info.name}}</td>
                      <td>{{info.member_price}}</td>
                      <td>{{info.non_member_price}}</td>
                    {% endif %}
                  {% endfor %}
                </tr>
            {% endfor %}
            </tbody>
          </table>
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
