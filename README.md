**Introduction**

The purpose of the "MIxS as RDF" project / codesite is to act as a repository for an RDF representation of the MIxS checklists.    The outputs presented here were constructed using the same processing techniques that were used to generate the Darwin Core RDF file, and hence look similar and are constructed in a similar manner.  Work on this project was suggested initially through the genomic biodiversity working group efforts and completed at the March 26-29 Seattle RCN4GSC/EAGER workshop.   

MIxS as RDF is an implementation of the MIxS standard and not an official GSC standard on its own.  The purpose of MIxS as RDF is to: 
  * Present in a useable manner the results of DwC/MIxS alignment efforts undertaken by GBWG in the last 18 months.
  * Enable DwC Extensions to be built around the notion of DNATissue and Sample.
  * Enable linked data views on MIxS data.

Some useful links:
  * [http://gensc.org/ns/mixs/index.html Web pages describing the MIxS As RDF terms]
  * [https://github.com/pyilmaz/mixs-as-rdf/blob/master/rdf/mixsterms_owl.rdf MIxS As RDF terms using OWL syntax, viewable in Protege]
  * [http://bioportal.bioontology.org/ontologies/3215 MIxS As RDF in BioPortal, which only lists "classes", not "properties".  It links to the RDF file in the preceding bullet point.]

**Namespace/Term Naming**

The process we undertook to map the existing MIxS terms, which exist as a checklist of terms without URI references, is clarified here.    The first step we undertook was to map ALL of the MIxS terms to be represented as URIs, such as changing health_disease_status to http://gensc.org/ns/mixs/healthDiseaseStatus.   The second step was, where those terms that directly map to DwC terms, we proposed the DwC term.    In cases where a DwC URI is used in place of the newly minted MIxS URI, we created a mapping between the older term and the newer term.  The relevant points we undertook are:

  *  All Original MIxS terms, taken from the the version 2 of the MIxS checklists, are alive and functional using the label_insdc field.  This means no change to current business is required.
  * The terms use the namespace http://gensc.org/ns/mixs/{term}.  Currently, this namespace does not link anywhere but we can easily fix this by putting a redirect on the gensc.org page.
  * All terms were modified to conform to RDF naming conventions in the RDF file.   The MIxS naming policy uses underscores to separate words, while the RDF file removes the underscore and capitalizes the first letter of all words, except the first.  So, "experimental_factor" becomes "experimentalFactor"
  * Some names were altered to in addition to re-use the DwC name:
    * project_name = http://rs.tdwg.org/dwc/terms/datasetName
    * source_mat_id = http://rs.tdwg.org/dwc/terms/MaterialSampleID
    * url = http://rs.tdwg.org/dwc/terms/associatedReferences
    * collection_date = http://rs.tdwg.org/dwc/terms/eventDate
    * isol_growth_condt = http://rs.tdwg.org/dwc/terms/samplingProtocol
    * lat_lon = http://rs.tdwg.org/dwc/terms/verbatimCoordinates
    * depth = http://rs.tdwg.org/dwc/terms/verbatimDepth
    * alt_elev = http://rs.tdwg.org/dwc/terms/verbatimElevation
    * geo_loc_name = http://rs.tdwg.org/dwc/terms/locality

**Classes**

MIxS does not define official classes but we opted to create them to conform to the DwC approach.  There are no domains/ranges defined here, so the classes are meant to designate logical groupings of properties only.   The defined classes are:

  * MaterialSample (proposed class in new MIxS ticket)
  * Occurrence (Represents MIxS properties falling under this DwC class)
  * Event (Represents MIxS properties falling under this DwC class)
  * dcterms:Location (Represents MIxS properties falling under this DwC class)
  * Investigation  (adapted from MIxS "Section Text")
  * Environment  (adapted from MIxS "Section Text")
  * Nucleic Acid Sequence Source  (adapted from MIxS "Section Text")
  * Sequencing  (adapted from MIxS "Section Text")
