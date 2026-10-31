---
layout: page
title: Discussion
permalink: /discussion.html
---

<div class="shadow-sm p-4 my-4" style="background-color: #E8F5E9; border-left: 6px solid #388E3C; border-radius: .25rem;">

<h3 style="color: #1B5E20;"> Explore the conversations, debates, and critical perspectives
that shaped the 1975 Speak-Out! symposium.</h3>

<p style="color: #1B3320; text-indent: 30px; margin-bottom: 1.5rem;">
For Discussion, Julia Dawson’s photographs examine the symposium’s panels on literature and art criticism and the diversity of the figures in conversation. In the photos taken at “Literary Criticism: Its Present Status in Latin America”, users can see literary critics from Brazil, Mexico, Peru, Chile, Argentina, and the United States, representing universities including the Catholic University of Rio de Janeiro, Indiana University, the University of Washington, and the University of Texas at Austin itself, in conversation with each other and with panel attendees. We see speakers captured mid-panel, alongside audience members in various states of attention, some rapt in their gaze upon the speakers, some consulting notes and programs, but all engaged with the subject of the panel in one form or another.  
</p>

<p style="color: #1B3320; text-indent: 30px; margin-bottom: 1.5rem;">
Meanwhile, at the panel "With What Operative Models, Local and Imported, Does the Latin American Plastic Artist Face His Circumstances;  and With What Sort of Critical Feedback Is He Faced?", a variety of international universities come together through representative critics and directors, including Jorge Alberto Manrique of the National University of Mexico, Aracy Amaral of the University of São Paulo, Brazil, and panel chairman Donald B. Goodall of the University of Texas. They present alongside artists including Rufino Tamayo from Mexico, Leonel Góngora of Colombia, and Alejandro Otero from Venezuela. As with the literary-criticism panel, a variety of Latin American perspectives are brought together, but in the context of a United States university with United States faculty and educators. In context, outside influence is unavoidable. 
</p>

</div>

<div class="container my-5">
  <div class="row justify-content-center">
    <div class="col-md-10">

      {% assign photo_ids = "img20251020_13271537,img20251020_13331931,img20251020_13390300,img20251020_13463883,img20251020_13472358,img20251020_13480757,img20251020_13484992,img20251020_13493301,img20251020_13501691,img20251020_13510163,img20251020_13522728,img20251020_13543929,img20251020_14012705,img20251020_14020918,img20251020_14081298,img20251020_14085738,img20251020_14094278,img20251020_14125114,img20251020_14133344,img20251020_14141474,img20251020_15123416,img20251020_15193125" | split: "," %}

      {% for photo_id in photo_ids %}
        {% assign item = site.data.speakoutmetadata | where: "objectid", photo_id | first %}

        {% if item %}
          <div class="mb-5">
            <img src="{{ '/assets/img/' | append: photo_id | append: '.jpg' | relative_url }}"
                 class="img-fluid w-100"
                 alt="{{ item.title }}">

            <h4 class="text-center mt-3">
              {{ item.title }}
            </h4>
          </div>
        {% endif %}

      {% endfor %}

    </div>
  </div>
</div>

</div>
