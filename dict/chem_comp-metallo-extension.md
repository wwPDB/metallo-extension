# Metallic ligand annotation update documentation

---
Title: Introduction to metallic ligand annotation dictionary extension  
Author: A. Biester, E. Peisach  
Date: 21-Apr-2025  
email: ezra.peisach@rcsb.org  
---
# Metallic ligand annotation update on Chemical Component Dictionary

This document provides an overview of extensions to support metallic ligand data
annotation and remediation. Listed below are dictionary content unique to metallic ligands,
either as new or updated data items within the exsiting dictionaries, or as new categories.

## chem_comp
Data items in the CHEM_COMP category give details about each
of the chemical components from which the relevant chemical
structures can be constructed, such as name, mass or charge.

The related categories CHEM_COMP_ATOM, CHEM_COMP_BOND,
CHEM_COMP_ANGLE etc. describe the detailed geometry of these
chemical components.


* **_chem_comp.pdbx_comp_type**
: A type classification of this chemical component.

    *Enumeration:*

      * metal cation
      * metal-containing ligand


## chem_comp_bond
Data items in the CHEM_COMP_BOND category record details about
the bonds between atoms in a chemical component. Target values
may be specified as bond orders, as a distance between the two
atoms, or both.


* **_chem_comp_bond.pdbx_metal_coordination_flag**
: This data item identifies if this is a bond between a metal and its coordinating group, otherwise
referred to as a dative or coordinate covalent bond. This flag is used for all bonds between
	       metals and non-metals, including metal-pi bonds and all other metal coordination bonds.

    *Enumeration:*

      * N
      * Y


* **_chem_comp_bond.pdbx_metal_pi_flag**
: This data item identifies if this is a bond between a metal and a pi system (alkene, arene, etc).

    *Enumeration:*

      * N
      * Y


## pdbx_chem_comp_atom_feature
Data items in the PDBX_CHEM_COMP_ATOM_FEATURE category provide
a selected list of atom level features for the chemical component.


* **_pdbx_chem_comp_atom_feature.ordinal**
: An ordinal index for this category


* **_pdbx_chem_comp_atom_feature.id**
: This data item is used to group together a corresponding
coordination number, coordination geometry, and
coordination descriptor for a given atom. A different id
is used to describe each unique group of coordination
number, coordination geometry, and coordination
descriptor.


* **_pdbx_chem_comp_atom_feature.comp_id**
: This data item is a pointer to _chem_comp_atom.comp_id in the CHEM_COMP
category.


* **_pdbx_chem_comp_atom_feature.atom_id**
: The identifier for the target atom to which the feature is assigned.


* **_pdbx_chem_comp_atom_feature.type**
: The feature assigned to this atom.

    *Enumeration:*

      * Coordination number
      * Coordination descriptor
      * Coordination geometry


* **_pdbx_chem_comp_atom_feature.value**
: The feature assigned to this atom.


* **_pdbx_chem_comp_atom_feature.provenance**
: The provenace of the feature assigned to this atom.

    *Enumeration:*

      * PDB
      * Author
      * FindGeo
      * MetalCoord


## pdbx_chem_comp_pcm
Data items in the PDBX_CHEM_COMP_PCM category provide
information about the protein modifications that are described
by the chemical component.


* **_pdbx_chem_comp_pcm.category**
: The category of protein modification.

    *Enumeration:*

      * Metal coordination
      * ...


## pdbx_chem_comp_precursor_set
Data items in the PDBX_CHEM_COMP_PRECURSOR_SET category describes
a set of precursors in the PDBX_CHEM_COMP_PRECURSOR category


* **_pdbx_chem_comp_precursor_set.id**
: An ordinal index for this category


* **_pdbx_chem_comp_precursor_set.class**
: The class of reaction that precursor set undergoes to produce final compound

    *Enumeration:*

      * Cyclization
      * Addition
      * Ring opening
      * Redox
      * Substitution
      * Multi-step
      * Elimination


* **_pdbx_chem_comp_precursor_set.details**
: Details about the precursor set


## pdbx_chem_comp_precursor
Data items in the PDBX_CHEM_COMP_PRECURSOR category describes
precursors for compounds that undergo a substantial chemical
	       change (>= 2 non-hydrogen leaving atoms, bond order change, metal
	       coordination change) in the macromolecular environmentprovide


* **_pdbx_chem_comp_precursor.id**
: An ordinal index for this category


* **_pdbx_chem_comp_precursor.comp_id**
: This data item is a pointer to id in the CHEM_COMP
category.


* **_pdbx_chem_comp_precursor.set_id**
: This data item is a pointer to id in the PDBX_CHEM_COMP_SET
category.


* **_pdbx_chem_comp_precursor.precursor_comp_id**
: This data item specifies the id in the CHEM_COMP category of the precursor.


* **_pdbx_chem_comp_precursor.formula**
: The formula for the chemical component. Formulae are written
according to the following rules:

(1) Only recognized element symbols may be used.

(2) Each element symbol is followed by a 'count' number. A count
of '1' may be omitted.

(3) A space or parenthesis must separate each cluster of
(element symbol + count), but in general parentheses are
not used.

(4) The order of elements depends on whether carbon is
present or not. If carbon is present, the order should be:
C, then H, then the other elements in alphabetical order
of their symbol. If carbon is not present, the elements
are listed purely in alphabetic order of their symbol. This
is the 'Hill' system used by Chemical Abstracts.


* **_pdbx_chem_comp_precursor.details**
: Details on the chemical component precursor.


## pdbx_chem_comp_precursor_descriptor
Data items in the PDBX_CHEM_COMP_PRECURSOR_DESCRIPTOR category
provide programatic descriptors for precursors


* **_pdbx_chem_comp_precursor_descriptor.ordinal**
: An ordinal index for this category


* **_pdbx_chem_comp_precursor_descriptor.comp_id**
: This data item is a pointer to id in the CHEM_COMP
category.


* **_pdbx_chem_comp_precursor_descriptor.precursor_id**
: This data item is a pointer to id in the PDBX_CHEM_COMP_PRECURSOR
category.


* **_pdbx_chem_comp_precursor_descriptor.type**
: This data item contains the precursor descriptor type.

    *Enumeration:*

      * InChI_STEREO
      * InChIKey
      * InChI_FIXEDH
      * InChI_CHARGE
      * InChI_MAIN_HATOM
      * SMILES
      * InChI_RECONNECT
      * InChI
      * InChI_MAIN
      * InChI_ISOTOPE
      * InChI_MAIN_FORMULA
      * SMILES_CANNONICAL
      * InChI_MAIN_CONNECT
      * SMILES_CANONICAL


* **_pdbx_chem_comp_precursor_descriptor.descriptor**
: This data item contains the descriptor value for this
precursor component.


* **_pdbx_chem_comp_precursor_descriptor.source**
: This data item contains the source of the descriptor value for this
component. This data item is used when the descriptor is obtained from the author,
	       by search in a database, or from another source (not directly computed).

    *Enumeration:*

      * CAS
      * PDB
      * Author
      * ChEMBL
      * ChEBI
      * PubChem


* **_pdbx_chem_comp_precursor_descriptor.source_version**
: This data item contains the version number of the source
of the decriptor value for this component.


* **_pdbx_chem_comp_precursor_descriptor.program**
: This data item contains the name of the program
or library used to compute the descriptor. This data item is
	       used when the descriptor is directly computed.

    *Enumeration:*

      * DAYLIGHT
      * OpenEye OEToolkits
      * InChI
      * CACTVS
      * ACDLabs
      * OTHER


* **_pdbx_chem_comp_precursor_descriptor.program_version**
: This data item contains the version of the program
or library used to compute the precursor_descriptor.


## pdbx_chem_comp_precursor_identifier
Data items in the CHEM_COMP_PRECURSOR_IDENTIFIER category provide
identifiers for precursor chemical components.


* **_pdbx_chem_comp_precursor_identifier.ordinal**
: An ordinal index for this category


* **_pdbx_chem_comp_precursor_identifier.comp_id**
: This data item is a pointer to id in the CHEM_COMP
category.


* **_pdbx_chem_comp_precursor_identifier.precursor_id**
: This data item is a pointer to id in the PDBX_CHEM_COMP_PRECURSOR
category.


* **_pdbx_chem_comp_precursor_identifier.type**
: This data item contains the precursor descriptor type.

    *Enumeration:*

      * MDL Identifier
      * SNFG CARBOHYDRATE SYMBOL
      * IUPAC CARB SYMBOL
      * IUPAC CARBOHYDRATE SYMBOL
      * COMMON NAME
      * CAS REGISTRY NUMBER
      * CONDENSED IUPAC CARBOHYDRATE SYMBOL
      * CONDENSED IUPAC CARB SYMBOL
      * SNFG CARB SYMBOL
      * SYNONYM
      * SYSTEMATIC NAME
      * PUBCHEM Identifier


* **_pdbx_chem_comp_precursor_identifier.identifier**
: This data item contains the identifier value for this
precursor component.


* **_pdbx_chem_comp_precursor_identifier.source**
: This data item contains the source of the identifier value for this
component. This data item is used when the identifier is obtained
	       from the author, by search in a database, or from another source (not directly computed).

    *Enumeration:*

      * CAS
      * PDB
      * Author
      * ChEMBL
      * ChEBI
      * PubChem


* **_pdbx_chem_comp_precursor_identifier.source_version**
: This data item contains the version number of the source
of the decriptor value for this component.


* **_pdbx_chem_comp_precursor_identifier.program**
: This data item contains the name of the program
or library used to compute the identifier. This data item is used
	       when the identifier is directly computed.

    *Enumeration:*

      * ChemDraw
      * DAYLIGHT
      * OpenEye OEToolkits
      * Lexichem
      * BIOVIA
      * Chemaxon
      * ACDLabs


* **_pdbx_chem_comp_precursor_identifier.program_version**
: This data item contains the version of the program
or library used to compute the precursor_identifier.



# Metallic ligand annotation update in PDB model coordinates files

## pdbx_modification_feature
Data items in the PDBX_MODIFICATION_FEATURE category provides
information about all the protein modifications that have been
modeled in the entry.


* **_pdbx_modification_feature.category**
: The category of protein modification.

    *Enumeration:*

      * Metal coordination
      * ...


## pdbx_nonpoly_feature
Data items in the PDBX_NONPOLY_FEATURE category provide
a selected list of atom level features for the chemical component.


* **_pdbx_nonpoly_feature.ordinal**
: An ordinal index for this category


* **_pdbx_nonpoly_feature.comp_id**
: This data item is a pointer to id in the CHEM_COMP
category.


* **_pdbx_nonpoly_feature.label_asym_id**
: The identifier of the instance of the STRUCT_ASYM_ID to which this feature applies.


* **_pdbx_nonpoly_feature.type**
: The feature assigned to this atom.

    *Enumeration:*

      * Group charge


* **_pdbx_nonpoly_feature.value**
: The feature assigned to this atom.


* **_pdbx_nonpoly_feature.provenance**
: The feature assigned to this atom.

    *Enumeration:*

      * PDB
      * Author


## pdbx_nonpoly_feature_evidence
Data items in the PDBX_NONPOLY_FEATURE_EVIDENCE category provide
a selected list of asym level features for the chemical component.


* **_pdbx_nonpoly_feature_evidence.ordinal**
: An ordinal index for this category


* **_pdbx_nonpoly_feature_evidence.comp_id**
: This data item is a pointer to id in the CHEM_COMP
category.


* **_pdbx_nonpoly_feature_evidence.label_asym_id**
: The identifier of the instance of the STRUCT_ASYM_ID to which this feature applies.


* **_pdbx_nonpoly_feature_evidence.type**
: The feature assigned to this atom.

    *Enumeration:*

      * Group charge


* **_pdbx_nonpoly_feature_evidence.experimental_support**
: The feature assigned to this atom.

    *Enumeration:*

      * Electron paramagnetic resonance spectroscopy
      * UV-Vis spectroscopy
      * Mossbauer spectroscopy
      * Other


* **_pdbx_nonpoly_feature_evidence.details**
: Additional details on this atom assignment


## pdbx_nonpoly_atom_feature
Data items in the PDBX_NONPOLY_ATOM_FEATURE category provide
a selected list of atom level features for the chemical component.


* **_pdbx_nonpoly_atom_feature.ordinal**
: An ordinal index for this category


* **_pdbx_nonpoly_atom_feature.comp_id**
: This data item is a pointer to id in the CHEM_COMP
category.


* **_pdbx_nonpoly_atom_feature.atom_id**
: The identifier for the target atom to which the feature is assigned.


* **_pdbx_nonpoly_atom_feature.label_asym_id**
: The identifier of the instance of the STRUCT_ASYM_ID to which this feature applies.


* **_pdbx_nonpoly_atom_feature.type**
: The feature assigned to this atom.

    *Enumeration:*

      * Coordination number
      * Coordination descriptor
      * Coordination geometry
      * Oxidation state


* **_pdbx_nonpoly_atom_feature.value**
: The feature assigned to this atom.


* **_pdbx_nonpoly_atom_feature.provenance**
: The feature assigned to this atom.

    *Enumeration:*

      * PDB
      * Author
      * FindGeo
      * MetalCoord


* **_pdbx_nonpoly_atom_feature.assessment**
: This data item provides an assessment of the value for the given
feature type (ex. coordination geometry). For
coordination geometry, the assessment is based on
comparison with the CCD. If features are annotated in
the CCD, then these features in the structure will be
compared with the references in the CCD. If there is a
match with the reference CCD, assessment will be
annotated as expected, whereas if there is not a match,
assessment will be annotated as unexpected.

    *Enumeration:*

      * No reference
      * Unexpected
      * Expected


## pdbx_nonpoly_atom_feature_evidence
Data items in the PDBX_NONPOLY_ATOM_FEATURE_EVIDENCE category provide
a selected list of atom level features for the chemical component.


* **_pdbx_nonpoly_atom_feature_evidence.ordinal**
: An ordinal index for this category


* **_pdbx_nonpoly_atom_feature_evidence.comp_id**
: This data item is a pointer to id in the CHEM_COMP
category.


* **_pdbx_nonpoly_atom_feature_evidence.atom_id**
: The identifier for the target atom to which the feature is assigned.


* **_pdbx_nonpoly_atom_feature_evidence.label_asym_id**
: The identifier of the instance of the STRUCT_ASYM_ID to which this feature applies.


* **_pdbx_nonpoly_atom_feature_evidence.type**
: The feature assigned to this atom.

    *Enumeration:*

      * Coordination number
      * Coordination geometry
      * Oxidation state
      * Metal identity


* **_pdbx_nonpoly_atom_feature_evidence.experimental_support**
: The feature assigned to this atom.

    *Enumeration:*

      * Electron paramagnetic resonance spectroscopy
      * Mossbauer spectroscopy
      * X-ray fluorescence
      * Raman spectroscopy
      * UV-Vis spectroscopy
      * Infrared spectroscopy
      * Anomalous scattering
      * X-ray absorption spectroscopy
      * Inductively coupled plasma mass spectrometry
      * Other


* **_pdbx_nonpoly_atom_feature_evidence.details**
: Additional details on this atom assignment






