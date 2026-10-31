---
layout: page
title: Exhibition
permalink: /exhibition.html
---

<div class="shadow-sm p-4 my-4" style="background-color: #FFF3E0; border-left: 6px solid #FF6F00; border-radius: .25rem;">

<h3 style="color: #FF6F00;"> Explore the Plural: Artists of Latin America exhibition
and the artworks presented.</h3>

<p style="color: #1B3320; text-indent: 30px; margin-bottom: 1.5rem;">
The theme with the most items, Exhibition, covers the Plural galleries and the artworks they display. The Exhibition’s artworks (arranged into sections by artist with the artist’s name and country of origin as the title of each gallery) are framed against massive white walls, by themselves or alongside others, sometimes with the works of the other artists visible in the background, but always with the greater context of the exhibition in mind. The artwork represents a dozen painters and sculptors originating or working in Latin America, all of whom were selected by Plural Editor-in-Chief Kazuya Sakai and UT-Austin visiting Professor Damián Bayón. This group includes sculptors and painters, most originating in Latin America, but with Brian Nissen born in England, Roger von Gunten from Switzerland, and Vicente Rojo from Spain (the art criticism panel places Spain in the same cultural and critical set with Latin American countries, but Rojo’s presence still demonstrates outside influence), all living and working in Mexico. The choices represent a region pushing to define its own identity in terms of art as well as art criticism, yet with the influence of the outside world (and Europe in particular) never far away. The same story is visible stylistically, with local cultural influences and art movements like Neo-Concrete Constructivism blending with global styles like Kinetic Art, Cubism, and Abstraction.
</p>
</div>
<div class="container my-5">
    <div class="row justify-content-center">
        <div class="exh-md-10">
    <div id="discussion-gallery"></div>        
    </div>
  </div>
</div>

<script src="{{ '/assets/lib/papaparse.min.js' | relative_url }}"></script>

<script>
document.addEventListener("DOMContentLoaded", function () {

  const photoIds = [
    "img20251013_10000401",
    "img20251013_10010858",
    "img20251013_10022473",
    "img20251013_10033477",
    "img20251013_10043843",
    "img20251013_10062097",
    "img20251013_10073012",
    "img20251013_10083894",
    "img20251013_10095103",
    "img20251013_10114027",
    "img20251013_10130363",
    "img20251013_10141266",
    "img20251009_16091030",
    "img20251009_16102360",
    "img20251009_16114389",
    "img20251009_16130867",
    "img20251009_16151273",
    "img20251009_16162208",
    "img20251009_16173983",
    "img20251009_16190400",
    "img20251009_15425492",
    "img20251009_15450963",
    "img20251009_15491837",
    "img20251009_15505594",
    "img20251009_15520771",
    "img20251009_15532355",
    "img20251009_15552231",
    "img20251009_15573867",
    "img20251009_16013822",
    "img20251009_16031756",
    "img20251009_16043979",
    "img20251009_16062949",
    "img20251009_16235460",
    "img20251009_16250943",
    "img20251009_16285115",
    "img20251009_16301573",
    "img20251009_16313481",
    "img20251009_16325969",
    "img20251009_16342173",
    "img20251009_16355402",
    "img20251009_16371569",
    "img20251009_16385057",
    "img20251009_16401463",
    "img20251009_16412713",
    "img20251013_09382917",
    "img20251013_09402267",
    "img20251013_09414794",
    "img20251013_09430541",
    "img20251013_09450207",
    "img20251013_09462217",
    "img20251013_09481729",
    "img20251013_09495475",
    "img20251013_09513914",
    "img20251013_09531375",
    "img20251013_09555639",
    "img20251013_09571853"
  ];

  const gallery = document.getElementById("exhibition-gallery");

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
      console.error("Could not load exhibition metadata:", error);
      gallery.textContent = "Unable to load photograph metadata.";
    }
  });

});
</script>
