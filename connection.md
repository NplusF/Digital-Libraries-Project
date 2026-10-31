---
layout: page
title: Connection
permalink: /connection.html
---
<div class="shadow-sm p-4 my-4" style="background-color: #E3F2FD; border-left: 6px solid #1976D2; border-radius: .25rem;">

<h3 style="color: #0D47A1;">Explore the Plural: Artists of Latin America exhibition and the artworks presented.</h3>

{% include feature/image.html objectid="img20251009_16371569" %}

<p style="color: #17324D; text-indent: 30px; margin-bottom: 1.5rem;">
	Finally, the theme of Connection uses the exhibition’s reception to explore the interactions between artists, critics, and panel speakers. Kazuya Sakai converses with Donald B. Goodall, Rodolfo Cardona the Chairman and Professor of the Department of Spanish and Portuguese at UT-Austin interacts with guests alongside Aracy Amaral, and attendees of all kinds interact and share the experience of the symposium and exhibition with each other. Even without the context of the spoken word, communication is visible, guests smiling at Mexican artist Helen Escobedo, Donald B. Goodall shaking the hands of attendees. The art itself remains visible in some shots, the direct subject of guest attention and conversation in some shots, the subject matter of the exhibition in perpetual conversation with all involved. Here, the worlds of art, criticism, and wider cultural understanding mix, and while the meetings present may not have the structure of the symposium proper, they bear the potential for Latin American artistic identity alongside the seeming inevitability of outside influence. 

</p>

</div>

<div class="container my-5">
  <div class="row justify-content-center">
    <div class="col-md-10">
      <div id="gallery"></div>
    </div>
  </div>
</div>

<script src="{{ '/assets/lib/papaparse.min.js' | relative_url }}"></script>

<script>
document.addEventListener("DOMContentLoaded", function () {

  const photoIds = [
    "img20251009_15110291",
    "img20251009_15120695",
    "img20251009_15124041",
    "img20251009_15131198",
    "img20251009_15134186",
    "img20251009_15141257",
    "img20251009_15151652",
    "img20251009_15204746",
    "img20251009_15211741",
    "img20251009_15214822",
    "img20251009_15280591",
    "img20251009_15290994",
    "img20251009_15294321",
    "img20251009_14390373",
    "img20251009_14393443",
    "img20251009_14403853",
    "img20251009_14414285",
    "img20251009_14421261",
    "img20251009_14431496",
    "img20251009_14445190",
    "img20251009_14465633",
    "img20251009_14472972"
  ];

  const gallery = document.getElementById("gallery");

  const csvUrl = "{{ '/assets/speakoutmetadata.csv' | relative_url }}";

  Papa.parse(csvUrl, {
    download: true,
    header: true,
    skipEmptyLines: true,

    complete: function(results) {
      const records = results.data;

      photoIds.forEach(function(id) {

        const item = records.find(function(row) {
          return row.objectid &&
                 row.objectid.trim() === id;
        });

        if (!item) {
          console.warn("Metadata not found for:", id);
          return;
        }

        const wrapper = document.createElement("div");
        wrapper.className = "mb-5 text-center";

        const img = document.createElement("img");
        img.src = "{{ '/assets/img/' | relative_url }}" + id + ".jpg";
        img.alt = item.title || "";
        img.className = "img-fluid";
        img.style.width = "75%";
        img.style.height = "auto";

        img.onerror = function() {
          console.error("Image could not be loaded:", img.src);
          wrapper.innerHTML = "Image not found: " + id;
        };

        const heading = document.createElement("h4");
        heading.className = "mt-3";
        heading.textContent = item.title || "";

        wrapper.appendChild(img);
        wrapper.appendChild(heading);
        gallery.appendChild(wrapper);

      });
    },

    error: function(error) {
      console.error("Could not load metadata:", error);
      gallery.textContent = "Unable to load photograph metadata.";
    }
  });

});
</script>
