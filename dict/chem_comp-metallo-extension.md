# Metallic ligand annotation update documentation

---
Title: Introduction to metallic ligand annotation dictionary extension  
Author: A. Biester, E. Peisach  
Date: 21-Aug-2025  
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

      * metal-containing ligand
      * metal cation


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


## pdbx_chem_comp_atom_coordination
Data items in the PDBX_CHEM_COMP_ATOM_COORDINATION category provide
coordination information on selected atoms


* **_pdbx_chem_comp_atom_coordination.geometry_id**
: This data item is used to group together equivalent geometries coming from different
software programs. For instance, if one program has an output of 'tetrahedral' and
another has an output of 'tetrahedron' for the same atom, these two records will
have the same geometry_id because these two outputs represent the same coordination geometry.


* **_pdbx_chem_comp_atom_coordination.comp_id**
: This data item is a pointer to _chem_comp_atom.comp_id in the CHEM_COMP
category.


* **_pdbx_chem_comp_atom_coordination.atom_id**
: The identifier for the target atom to which the feature is assigned.


* **_pdbx_chem_comp_atom_coordination.number**
: The coordination number of the target atom.


* **_pdbx_chem_comp_atom_coordination.geometry**
: This data item contains the geometry output from a software program (for example, FindGeo or MetalCoord).


* **_pdbx_chem_comp_atom_coordination.geometry_generic**
: This data item translates the geometry output from a software program (for example, FindGeo or MetalCoord) into
a unified naming scheme. As software programs sometimes have different names for the same geometry (for instance,
	       'tetrahedral' and 'tetrahedron' correspond to the same geometry), this data item provides a name for
	       the geometry that is consistent regardless of the provenance to enhance findability.

    *Enumeration:*

      * cubic with vacancy
      * sandwich 5 4 i
      * hexagonal planar
      * sandwich 5 4
      * trigonal pyramidal
      * sandwich 8 8
      * sandwich 6 5
      * trigonal prism tricapped
      * trigonal planar tricapped
      * paired octahedral
      * sandwich 4h 2
      * sandwich 5 5 v i
      * sandwich 6 6
      * square non-planar
      * square planar bicapped
      * sandwich 5 2
      * sandwich 5h 3
      * pentagonal bipyramidal
      * square antiprismatic
      * sandwich 6 3
      * penta trigonal planar
      * sandwich 5 square pyramidal monocapped
      * ball
      * sandwich 5 3
      * sandwich 5 pentagonal pyramidal
      * t shape
      * sandwich 8 8 i
      * sandwich 6 2
      * trigonal planar monocapped
      * penta trigonal planar i
      * sandwich 5 tricapped i
      * sandwich 5 capped 1
      * sandwich 6 4
      * sandwich 4 2
      * square pyramidal
      * square planar
      * trigonal prismatic all face capped
      * linear
      * sandwich 8 8 v
      * sandwich 6 5 v
      * square planar monocapped
      * trigonal planar bicapped
      * sandwich 4h 4
      * sandwich 5 hexagonal pyramidal
      * bent
      * trigonal prismatic monocapped with vacancy
      * trigonal bipyramidal with vacancy
      * sandwich 4h 3
      * sandwich 8 5 i
      * tetrahedral
      * square antiprismatic monocapped
      * octahedral monocapped with vacancy
      * square antiprismatic bicapped
      * sandwich 4 3
      * hexagonal bipyramidal with vacancy
      * trigonal planar
      * cubic
      * sandwich 5 square pyramidal
      * sandwich 8 3
      * sandwich 4h 4h
      * linear monocapped
      * sandwich 5 4h
      * cuboctahedral
      * trigonal prismatic
      * pyramidal
      * sandwich 5 tricapped v
      * square pyramidal with vacancy
      * hexagonal bipyramidal
      * sandwich 5 1
      * sandwich 5 4h v
      * pentagonal bipyramidal with vacancy
      * trigonal bipyramidal
      * linear bicapped
      * square antiprismatic with vacancy
      * sandwich 6 trigonal pyramidal
      * penta trigonal planar i i
      * sandwich 5 5 v v 3d
      * sandwich 5 5 4
      * sandwich c5 5 i
      * trigonal prismatic monocapped
      * sandwich 6 6 v
      * sandwich 6 6 triangle
      * sandwich 5 5o
      * dodecahedral
      * seamine
      * pentagonal antiprismatic
      * octahedral
      * penta trigonal planar v
      * trigonal prismatic bicapped
      * sandwich 7 5
      * sandwich 7 1
      * sandwich 6 1
      * octahedral bicapped
      * sandwich 8 4
      * pentagonal prismatic
      * trigonal prismatic with vacancy
      * sandwich 5 5
      * sandwich 7 3
      * irregular
      * sandwich 7 2
      * sandwich 5 5 v v
      * sandwich 5 5 star
      * sandwich 5 5 v
      * sandwich 8 5
      * octahedral monocapped
      * sandwich 5 5 i


* **_pdbx_chem_comp_atom_coordination.provenance**
: The provenance of the feature assigned to this atom.

    *Enumeration:*

      * MetalCoord
      * Author
      * PDB
      * FindGeo


* **_pdbx_chem_comp_atom_coordination.representative_entry_id**
: The representative entry for this set


## pdbx_chem_comp_atom_coordination_sphere
Data items in the PDBX_CHEM_COMP_ATOM_COORDINATION_SPHERE category provide
geometric coordination information on selected atoms


* **_pdbx_chem_comp_atom_coordination_sphere.id**
: An ordinal index for this category


* **_pdbx_chem_comp_atom_coordination_sphere.geometry_id**
: This data item is a foreign key to _pdbx_chem_comp_atom_coordination.geometry_id. This item maps the
coordination descriptor to a specific geometry described in the pdbx_chem_comp_atom_coordination category.


* **_pdbx_chem_comp_atom_coordination_sphere.comp_id**
: This data item is a pointer to _chem_comp_atom.comp_id in the CHEM_COMP
category.


* **_pdbx_chem_comp_atom_coordination_sphere.atom_id**
: The identifier for the target atom to which the feature is assigned.


* **_pdbx_chem_comp_atom_coordination_sphere.descriptor**
: A descriptor describing the geometry of this atom.


* **_pdbx_chem_comp_atom_coordination_sphere.provenance**
: The provenance of the feature assigned to this atom.

    *Enumeration:*

      * MetalCoord
      * PDB
      * FindGeo


* **_pdbx_chem_comp_atom_coordination_sphere.representative_entry_id**
: The representative entry for this set


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

## pdbx_nonpoly_atom_coordination
Data items in the PDBX_NONPOLY_ATOM_COORDINATION category provide
coordination information on selected atoms


* **_pdbx_nonpoly_atom_coordination.geometry_id**
: This data item is used to group together equivalent
geometries coming from different software programs.
	       For instance, if one program has an output of 'tetrahedral'
and another has an output of 'tetrahedron' for the same atom,
	       these two records will have the same geometry_id
	       because these two outputs represent the same coordination geometry.


* **_pdbx_nonpoly_atom_coordination.label_asym_id**
: The identifier of the instance of the STRUCT_ASYM_ID to which this feature applies.


* **_pdbx_nonpoly_atom_coordination.comp_id**
: This data item is a pointer to _chem_comp_atom.comp_id in the CHEM_COMP
category.


* **_pdbx_nonpoly_atom_coordination.atom_id**
: The identifier for the target atom to which the feature is assigned.


* **_pdbx_nonpoly_atom_coordination.alt_id**
: A place holder to indicate alternate conformation.


* **_pdbx_nonpoly_atom_coordination.number**
: The coordination number of the target atom.


* **_pdbx_nonpoly_atom_coordination.geometry**
: This data item translates the geometry output from a software
program (for example, FindGeo or MetalCoord) into a unified naming
	       scheme. As software programs sometimes have different names for
	       the same geometry (for instance, 'tetrahedral' and 'tetrahedron'
	       correspond to the same geometry), this data item provides a name
	       for the geometry that is consistent regardless of the provenance
	       to enhance findability.


* **_pdbx_nonpoly_atom_coordination.geometry_generic**
: This data item translates the geometry output from a software program (for example, FindGeo or MetalCoord) into
a unified naming scheme. As software programs sometimes have different names for the same geometry (for instance,
	       'tetrahedral' and 'tetrahedron' correspond to the same geometry), this data item provides a name for
	       the geometry that is consistent regardless of the provenance to enhance findability.

    *Enumeration:*

      * cubic with vacancy
      * sandwich 5 4 i
      * hexagonal planar
      * sandwich 5 4
      * trigonal pyramidal
      * sandwich 8 8
      * sandwich 6 5
      * trigonal prism tricapped
      * trigonal planar tricapped
      * paired octahedral
      * sandwich 4h 2
      * sandwich 5 5 v i
      * sandwich 6 6
      * square non-planar
      * square planar bicapped
      * sandwich 5 2
      * sandwich 5h 3
      * pentagonal bipyramidal
      * square antiprismatic
      * sandwich 6 3
      * penta trigonal planar
      * sandwich 5 square pyramidal monocapped
      * ball
      * sandwich 5 3
      * sandwich 5 pentagonal pyramidal
      * t shape
      * sandwich 8 8 i
      * sandwich 6 2
      * trigonal planar monocapped
      * penta trigonal planar i
      * sandwich 5 tricapped i
      * sandwich 5 capped 1
      * sandwich 6 4
      * sandwich 4 2
      * square pyramidal
      * square planar
      * trigonal prismatic all face capped
      * linear
      * sandwich 8 8 v
      * sandwich 6 5 v
      * square planar monocapped
      * trigonal planar bicapped
      * sandwich 4h 4
      * sandwich 5 hexagonal pyramidal
      * bent
      * trigonal prismatic monocapped with vacancy
      * trigonal bipyramidal with vacancy
      * sandwich 4h 3
      * sandwich 8 5 i
      * tetrahedral
      * square antiprismatic monocapped
      * octahedral monocapped with vacancy
      * square antiprismatic bicapped
      * sandwich 4 3
      * hexagonal bipyramidal with vacancy
      * trigonal planar
      * cubic
      * sandwich 5 square pyramidal
      * sandwich 8 3
      * sandwich 4h 4h
      * linear monocapped
      * sandwich 5 4h
      * cuboctahedral
      * trigonal prismatic
      * pyramidal
      * sandwich 5 tricapped v
      * square pyramidal with vacancy
      * hexagonal bipyramidal
      * sandwich 5 1
      * sandwich 5 4h v
      * pentagonal bipyramidal with vacancy
      * trigonal bipyramidal
      * linear bicapped
      * square antiprismatic with vacancy
      * sandwich 6 trigonal pyramidal
      * penta trigonal planar i i
      * sandwich 5 5 v v 3d
      * sandwich 5 5 4
      * sandwich c5 5 i
      * trigonal prismatic monocapped
      * sandwich 6 6 v
      * sandwich 6 6 triangle
      * sandwich 5 5o
      * dodecahedral
      * seamine
      * pentagonal antiprismatic
      * octahedral
      * penta trigonal planar v
      * trigonal prismatic bicapped
      * sandwich 7 5
      * sandwich 7 1
      * sandwich 6 1
      * octahedral bicapped
      * sandwich 8 4
      * pentagonal prismatic
      * trigonal prismatic with vacancy
      * sandwich 5 5
      * sandwich 7 3
      * irregular
      * sandwich 7 2
      * sandwich 5 5 v v
      * sandwich 5 5 star
      * sandwich 5 5 v
      * sandwich 8 5
      * octahedral monocapped
      * sandwich 5 5 i


* **_pdbx_nonpoly_atom_coordination.provenance**
: The provenance of the feature assigned to this atom.

    *Enumeration:*

      * MetalCoord
      * Author
      * PDB
      * FindGeo


* **_pdbx_nonpoly_atom_coordination.assessment**
: This data item provides an assessment of the coordination.
The assessment is based on comparison with the CCD. If coordination
	       is annotated in the CCD, then the coordination in the structure will
	       be compared with the reference(s) in the CCD. If there is a match
	       with the reference CCD, assessment will be annotated as Expected,
	       whereas if there is not a match, assessment will be annotated as Unexpected.
	       If there is no reference in the CCD, assessment will be annotated
	       as 'No reference'.

    *Enumeration:*

      * Expected
      * Unexpected
      * No reference


## pdbx_nonpoly_atom_coordination_sphere
Data items in the PDBX_NONPOLY_ATOM_COORDINATION_SPHERE category provide
geometric coordination information on selected atoms


* **_pdbx_nonpoly_atom_coordination_sphere.geometry_id**
: This data item is a foreign key to _pdbx_nonpoly_atom_coordination.geometry_id. This
item maps the coordination descriptor to a specific geometry described in the
pdbx_nonpoly_atom_coordination category.


* **_pdbx_nonpoly_atom_coordination_sphere.label_asym_id**
: The identifier of the instance of the STRUCT_ASYM_ID to which this feature applies.


* **_pdbx_nonpoly_atom_coordination_sphere.comp_id**
: This data item is a pointer to _chem_comp_atom.comp_id in the CHEM_COMP
category.


* **_pdbx_nonpoly_atom_coordination_sphere.alt_id**
: A place holder to indicate alternate conformation.


* **_pdbx_nonpoly_atom_coordination_sphere.atom_id**
: The identifier for the target atom to which the feature is assigned.


* **_pdbx_nonpoly_atom_coordination_sphere.descriptor**
: A descriptor describing the geometry of this atom.


* **_pdbx_nonpoly_atom_coordination_sphere.provenance**
: The provenance of the feature assigned to this atom.

    *Enumeration:*

      * MetalCoord
      * PDB
      * FindGeo


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

      * UV-Vis spectroscopy
      * Electron paramagnetic resonance spectroscopy
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

      * Oxidation state


* **_pdbx_nonpoly_atom_feature.value**
: The feature assigned to this atom.


* **_pdbx_nonpoly_atom_feature.provenance**
: The feature assigned to this atom.

    *Enumeration:*

      * Author
      * PDB


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

      * Oxidation state
      * Metal identity


* **_pdbx_nonpoly_atom_feature_evidence.experimental_support**
: The feature assigned to this atom.

    *Enumeration:*

      * UV-Vis spectroscopy
      * Anomalous scattering
      * Inductively coupled plasma mass spectrometry
      * Raman spectroscopy
      * X-ray absorption spectroscopy
      * Electron paramagnetic resonance spectroscopy
      * X-ray fluorescence
      * Infrared spectroscopy
      * Mossbauer spectroscopy
      * Other


* **_pdbx_nonpoly_atom_feature_evidence.details**
: Additional details on this atom assignment







