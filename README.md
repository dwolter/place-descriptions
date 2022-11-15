# Place Descriptions

This repository contains a dataset of place descriptions mainly collected from Wikipedia and travel blogs. Place descriptions typically consists out of one single sentence.

The directory *paraphrased* contains sentences containing paraphrased place descriptions. The idea of this dataset is to investigate means of identifying the type of place used in the OpenStreetMap database. To this end, we manually determined the ground truth (OSM tags) for the each place description. 

The file *descriptions.txt* contains a simple text-based format:
 - every line contains a single description
 - nouns with spatial interpretation that can be geo-referenced are tagged `(:spatial [:primary] <word1> [... <wordn>])`, where `:primary` designates the primary, i.e., key place, the sentence talks about. For example, in *The post office is located just across the street from Bamberg main station.* the tagging would be *The (:spatial :primary post office) is located just across the (:spatial street) from (:spatial Bamberg main station).* As can be seen, compound words are tagged as a single entity.

If you want to remove the tagging, you can use command-line tools such as sed:
 > sed 's|[(),]||g' descriptions.txt |  sed 's/:spatial//g' | sed 's/:primary//g' > descriptions_without_tags.txt
