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

      * Y
      * N


* **_chem_comp_bond.pdbx_metal_pi_flag**
: This data item identifies if this is a bond between a metal and a pi system (alkene, arene, etc).

    *Enumeration:*

      * Y
      * N


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

      * Coordination descriptor
      * Coordination geometry
      * Coordination number


* **_pdbx_chem_comp_atom_feature.value**
: The feature assigned to this atom.


* **_pdbx_chem_comp_atom_feature.provenance**
: The provenace of the feature assigned to this atom.

    *Enumeration:*

      * Author
      * FindGeo
      * PDB
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

      * Author
      * PDB


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

      * Other
      * Electron paramagnetic resonance spectroscopy
      * UV-Vis spectroscopy
      * Mossbauer spectroscopy


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

      * Coordination descriptor
      * Coordination geometry
      * Coordination number
      * Oxidation state


* **_pdbx_nonpoly_atom_feature.value**
: The feature assigned to this atom.


* **_pdbx_nonpoly_atom_feature.provenance**
: The feature assigned to this atom.

    *Enumeration:*

      * Author
      * FindGeo
      * PDB
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

      * Unexpected
      * No reference
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

      * Metal identity
      * Oxidation state


* **_pdbx_nonpoly_atom_feature_evidence.experimental_support**
: The feature assigned to this atom.

    *Enumeration:*

      * Electron paramagnetic resonance spectroscopy
      * X-ray absorption spectroscopy
      * X-ray fluorescence
      * Inductively coupled plasma mass spectrometry
      * Anomalous scattering
      * Infrared spectroscopy
      * Mossbauer spectroscopy
      * Raman spectroscopy
      * UV-Vis spectroscopy
      * Other


* **_pdbx_nonpoly_atom_feature_evidence.details**
: Additional details on this atom assignment






