# 082E-rosetta-scripts

Rosetta is the sample project for the DaSCH Service Platform. On the one hand, it is intended to illustrate the 
possibilities currently offered by the platform, but on the other hand, it also shows internally where there 
is still room for improvement.

## Basic usage
 - start a local DSP API as described [here](https://github.com/dasch-swiss/dsp-api#try-it-out)
 - install dsp-tools with `pip3 install dsp-tools`
 - create the ontologies `rosetta` and `rosetta2` with `dsp-tools create rosetta.json`
 - upload the first data file with `dsp-tools xmlupload rosetta.xml`

## Advanced usage
In the previous paragraph, you have populated the ontology "rosetta" with data from the file "rosetta.xml". 
However, there is also a second ontology, "rosetta2", which can be populated with data from "rosetta2.xml". 
But this file contains a resptr-prop link to an image from the first file: `img_obj_0`. 
In order to create this link, the ID `img_obj_0` has to be replaced by its IRI.  

The IRI is the identifier of an resource inside DSP. It was created during the upload and can now be retrieved 
in the DSP-APP or from "id2iri_rosetta_mapping_(timestamp).json".  

To upload "rosetta2.xml", do the following:
 - run `dsp-tools id2iri rosetta2.xml id2iri_rosetta_mapping_(timestamp).json`. 
 - A new file named "rosetta2_replaced_(timestamp).xml" will be created. It contains the IRI of `img_obj_0` instead of the old ID.
 - upload the second data file with `dsp-tools xmlupload --incremental rosetta2_replaced_(timestamp).xml`