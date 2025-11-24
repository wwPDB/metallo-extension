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
The geometry derived from observed geometries in atomic coordinate files.


* **_pdbx_chem_comp_atom_coordination.geometry_generic**
: This data item translates the geometry output from a software program (for example, FindGeo or MetalCoord) into
a unified naming scheme. As software programs sometimes have different names for the same geometry (for instance,
	       'tetrahedral' and 'tetrahedron' correspond to the same geometry), this data item provides a name for
	       the geometry that is consistent regardless of the provenance to enhance findability. The geometry derived
	       from observed geometries in atomic coordinate files.

    *Enumeration:*

      * ball
      * bent
      * cubic
      * cubic with vacancy
      * cuboctahedral
      * dodecahedral
      * hexagonal bipyramidal
      * hexagonal bipyramidal with vacancy
      * hexagonal planar
      * irregular
      * linear
      * linear bicapped
      * linear monocapped
      * octahedral
      * octahedral bicapped
      * octahedral monocapped
      * octahedral monocapped with vacancy
      * paired octahedral
      * penta trigonal planar
      * penta trigonal planar i
      * penta trigonal planar i i
      * penta trigonal planar v
      * pentagonal antiprismatic
      * pentagonal bipyramidal
      * pentagonal bipyramidal with vacancy
      * pentagonal prismatic
      * pyramidal
      * sandwich 4 2
      * sandwich 4 3
      * sandwich 4h 2
      * sandwich 4h 3
      * sandwich 4h 4
      * sandwich 4h 4h
      * sandwich 5 1
      * sandwich 5 2
      * sandwich 5 3
      * sandwich 5 4
      * sandwich 5 4 i
      * sandwich 5 4h
      * sandwich 5 4h v
      * sandwich 5 5
      * sandwich 5 5 4
      * sandwich 5 5 i
      * sandwich 5 5 star
      * sandwich 5 5 v
      * sandwich 5 5 v i
      * sandwich 5 5 v v
      * sandwich 5 5 v v 3d
      * sandwich 5 5o
      * sandwich 5 capped 1
      * sandwich 5 hexagonal pyramidal
      * sandwich 5 pentagonal pyramidal
      * sandwich 5 square pyramidal
      * sandwich 5 square pyramidal monocapped
      * sandwich 5 tricapped i
      * sandwich 5 tricapped v
      * sandwich 5h 3
      * sandwich 6 1
      * sandwich 6 2
      * sandwich 6 3
      * sandwich 6 4
      * sandwich 6 5
      * sandwich 6 5 v
      * sandwich 6 6
      * sandwich 6 6 triangle
      * sandwich 6 6 v
      * sandwich 6 trigonal pyramidal
      * sandwich 7 1
      * sandwich 7 2
      * sandwich 7 3
      * sandwich 7 5
      * sandwich 8 3
      * sandwich 8 4
      * sandwich 8 5
      * sandwich 8 5 i
      * sandwich 8 8
      * sandwich 8 8 i
      * sandwich 8 8 v
      * sandwich c5 5 i
      * seamine
      * square antiprismatic
      * square antiprismatic bicapped
      * square antiprismatic monocapped
      * square antiprismatic with vacancy
      * square non-planar
      * square planar
      * square planar bicapped
      * square planar monocapped
      * square pyramidal
      * square pyramidal with vacancy
      * t shape
      * tetrahedral
      * trigonal bipyramidal
      * trigonal bipyramidal with vacancy
      * trigonal planar
      * trigonal planar bicapped
      * trigonal planar monocapped
      * trigonal planar tricapped
      * trigonal prism tricapped
      * trigonal prismatic
      * trigonal prismatic all face capped
      * trigonal prismatic bicapped
      * trigonal prismatic monocapped
      * trigonal prismatic monocapped with vacancy
      * trigonal prismatic with vacancy
      * trigonal pyramidal


* **_pdbx_chem_comp_atom_coordination.geometry_abbr**
: This data item lists the abbreviated name of the geometry, as specified in the
_pdbx_chem_comp_atom_coordination_sphere.descriptor. For instance, square planar
	       is abbreviated to SPL. The geometry derived from observed geometries in atomic coordinate files.


* **_pdbx_chem_comp_atom_coordination.provenance**
: The provenance of the feature assigned to this atom.

    *Enumeration:*

      * Author
      * FindGeo
      * MetalCoord
      * PDB



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
: This data item contains a descriptor of the coordination environment of
an atom. The descriptor is derived from observed coordination environments
	       in atomic coordinate files.


* **_pdbx_chem_comp_atom_coordination_sphere.provenance**
: The provenance of the feature assigned to this atom.

    *Enumeration:*

      * FindGeo
      * MetalCoord
      * PDB



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


* **_pdbx_nonpoly_atom_coordination.label_seq_id**
: This data item is a pointer to _atom_site.label_seq_id in the
ATOM_SITE category.


* **_pdbx_nonpoly_atom_coordination.label_comp_id**
: This data item is a pointer to _atom_site.label_comp_id in the ATOM_SITE
category.


* **_pdbx_nonpoly_atom_coordination.label_atom_id**
: The identifier for the target atom to which the feature is assigned.


* **_pdbx_nonpoly_atom_coordination.label_alt_id**
: A place holder to indicate alternate conformation.


* **_pdbx_nonpoly_atom_coordination.auth_asym_id**
: A component of the identifier for the residue at which the
conformation segment begins.

This data item is a pointer to _atom_site.auth_asym_id in the
ATOM_SITE category.


* **_pdbx_nonpoly_atom_coordination.auth_seq_id**
: A component of the identifier for the residue at which the
conformation segment begins.

This data item is a pointer to _atom_site.auth_seq_id in the
ATOM_SITE category.


* **_pdbx_nonpoly_atom_coordination.auth_comp_id**
: A component of the identifier for the residue at which the
conformation segment begins.

This data item is a pointer to _atom_site.auth_comp_id in
the ATOM_SITE category.


* **_pdbx_nonpoly_atom_coordination.auth_atom_id**
: A component of the identifier for partner 1 of the structure
connection.

This data item is a pointer to _atom_site.auth_atom_id in the
ATOM_SITE category.


* **_pdbx_nonpoly_atom_coordination.PDB_ins_code**
: PDB insertion code.


* **_pdbx_nonpoly_atom_coordination.number**
: The coordination number of the target atom.


* **_pdbx_nonpoly_atom_coordination.geometry_calculated**
: This data item contains the geometry output from a software program
(for example, FindGeo or MetalCoord). The geometry is based on what
	       is observed in the coordinate file.


* **_pdbx_nonpoly_atom_coordination.software_remark**
: This data item describes the agreement of the
software-generated geometry with the idealized
reference geometries. This information is generated by
the software that generates geometry annotation.


* **_pdbx_nonpoly_atom_coordination.geometry_generic**
: This data item translates the geometry output from a
software program (for example, FindGeo or MetalCoord)
into a unified naming scheme. As software programs
sometimes have different names for the same geometry
(for instance, 'tetrahedral' and 'tetrahedron'
correspond to the same geometry), this data item
provides a name for the geometry that is consistent
regardless of the provenance to enhance
findability. The geometry is based on what is observed
in the coordinate file.

    *Enumeration:*

      * ball
      * bent
      * cubic
      * cubic with vacancy
      * cuboctahedral
      * dodecahedral
      * hexagonal bipyramidal
      * hexagonal bipyramidal with vacancy
      * hexagonal planar
      * irregular
      * linear
      * linear bicapped
      * linear monocapped
      * octahedral
      * octahedral bicapped
      * octahedral monocapped
      * octahedral monocapped with vacancy
      * paired octahedral
      * penta trigonal planar
      * penta trigonal planar i
      * penta trigonal planar i i
      * penta trigonal planar v
      * pentagonal antiprismatic
      * pentagonal bipyramidal
      * pentagonal bipyramidal with vacancy
      * pentagonal prismatic
      * pyramidal
      * sandwich 4 2
      * sandwich 4 3
      * sandwich 4h 2
      * sandwich 4h 3
      * sandwich 4h 4
      * sandwich 4h 4h
      * sandwich 5 1
      * sandwich 5 2
      * sandwich 5 3
      * sandwich 5 4
      * sandwich 5 4 i
      * sandwich 5 4h
      * sandwich 5 4h v
      * sandwich 5 5
      * sandwich 5 5 4
      * sandwich 5 5 i
      * sandwich 5 5 star
      * sandwich 5 5 v
      * sandwich 5 5 v i
      * sandwich 5 5 v v
      * sandwich 5 5 v v 3d
      * sandwich 5 5o
      * sandwich 5 capped 1
      * sandwich 5 hexagonal pyramidal
      * sandwich 5 pentagonal pyramidal
      * sandwich 5 square pyramidal
      * sandwich 5 square pyramidal monocapped
      * sandwich 5 tricapped i
      * sandwich 5 tricapped v
      * sandwich 5h 3
      * sandwich 6 1
      * sandwich 6 2
      * sandwich 6 3
      * sandwich 6 4
      * sandwich 6 5
      * sandwich 6 5 v
      * sandwich 6 6
      * sandwich 6 6 triangle
      * sandwich 6 6 v
      * sandwich 6 trigonal pyramidal
      * sandwich 7 1
      * sandwich 7 2
      * sandwich 7 3
      * sandwich 7 5
      * sandwich 8 3
      * sandwich 8 4
      * sandwich 8 5
      * sandwich 8 5 i
      * sandwich 8 8
      * sandwich 8 8 i
      * sandwich 8 8 v
      * sandwich c5 5 i
      * seamine
      * square antiprismatic
      * square antiprismatic bicapped
      * square antiprismatic monocapped
      * square antiprismatic with vacancy
      * square non-planar
      * square planar
      * square planar bicapped
      * square planar monocapped
      * square pyramidal
      * square pyramidal with vacancy
      * t shape
      * tetrahedral
      * trigonal bipyramidal
      * trigonal bipyramidal with vacancy
      * trigonal planar
      * trigonal planar bicapped
      * trigonal planar monocapped
      * trigonal planar tricapped
      * trigonal prism tricapped
      * trigonal prismatic
      * trigonal prismatic all face capped
      * trigonal prismatic bicapped
      * trigonal prismatic monocapped
      * trigonal prismatic monocapped with vacancy
      * trigonal prismatic with vacancy
      * trigonal pyramidal


* **_pdbx_nonpoly_atom_coordination.geometry_abbr**
: This data item lists the abbreviated name of the
geometry, as specified in the
_pdbx_nonpoly_atom_coordination_sphere.descriptor. For
instance, square planar is abbreviated to SPL. The
geometry derived from observed geometries in atomic
coordinate files.


* **_pdbx_nonpoly_atom_coordination.provenance**
: The provenance of the feature assigned to this atom.

    *Enumeration:*

      * Author
      * FindGeo
      * MetalCoord
      * PDB


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
      * No reference
      * Unexpected


## pdbx_nonpoly_atom_coordination_sphere
Data items in the PDBX_NONPOLY_ATOM_COORDINATION_SPHERE category provide
geometric coordination information on selected atoms


* **_pdbx_nonpoly_atom_coordination_sphere.id**
: This data item is the parent for
_pdbx_nonpoly_atom_coordination_sphere_order.sphere_id.


* **_pdbx_nonpoly_atom_coordination_sphere.geometry_id**
: This data item is a foreign key to _pdbx_nonpoly_atom_coordination.geometry_id. This
item maps the coordination descriptor to a specific geometry described in the
pdbx_nonpoly_atom_coordination category.


* **_pdbx_nonpoly_atom_coordination_sphere.label_asym_id**
: The identifier of the instance of the STRUCT_ASYM_ID to which this feature applies.


* **_pdbx_nonpoly_atom_coordination_sphere.label_seq_id**
: This data item is a pointer to _atom_site.label_seq_id in the
ATOM_SITE category.


* **_pdbx_nonpoly_atom_coordination_sphere.label_comp_id**
: This data item is a pointer to _atom_site.comp_id in the ATOM_SITE
category.


* **_pdbx_nonpoly_atom_coordination_sphere.label_atom_id**
: The identifier for the target atom to which the feature is assigned.


* **_pdbx_nonpoly_atom_coordination_sphere.label_alt_id**
: A place holder to indicate alternate conformation.


* **_pdbx_nonpoly_atom_coordination_sphere.auth_asym_id**
: A component of the identifier for the residue at which the
conformation segment begins.

This data item is a pointer to _atom_site.auth_asym_id in the
ATOM_SITE category.


* **_pdbx_nonpoly_atom_coordination_sphere.auth_seq_id**
: A component of the identifier for the residue at which the
conformation segment begins.

This data item is a pointer to _atom_site.auth_seq_id in the
ATOM_SITE category.


* **_pdbx_nonpoly_atom_coordination_sphere.auth_comp_id**
: A component of the identifier for the residue at which the
conformation segment begins.

This data item is a pointer to _atom_site.auth_comp_id in
the ATOM_SITE category.


* **_pdbx_nonpoly_atom_coordination_sphere.auth_atom_id**
: A component of the identifier for partner 1 of the structure
connection.

This data item is a pointer to _atom_site.auth_atom_id in the
ATOM_SITE category.


* **_pdbx_nonpoly_atom_coordination_sphere.PDB_ins_code**
: PDB insertion code.


* **_pdbx_nonpoly_atom_coordination_sphere.descriptor**
: This data item contains a descriptor of the coordination environment
of an atom. The descriptor is based on what is observed in the coordinate
	       file.


* **_pdbx_nonpoly_atom_coordination_sphere.provenance**
: The provenance of the feature assigned to this atom.

    *Enumeration:*

      * FindGeo
      * MetalCoord
      * PDB


## pdbx_nonpoly_atom_coordination_sphere_order
This category describes the order of the atoms in the
coordination sphere category:
pdbx_nonpoly_atom_coordination_sphere. The order of the
atoms is the encoding of the 3D arrangement of atoms
for a particular coordination geometry.


* **_pdbx_nonpoly_atom_coordination_sphere_order.sphere_id**
: This data item is a foreign key to
_pdbx_nonpoly_atom_coordination_sphere.id
This item maps the coordination sphere order to a
specific coordination sphere described in the
pdbx_nonpoly_atom_coordination_sphere category.


* **_pdbx_nonpoly_atom_coordination_sphere_order.label_asym_id**
: The identifier of the instance of the STRUCT_ASYM_ID to which this feature applies.


* **_pdbx_nonpoly_atom_coordination_sphere_order.label_seq_id**
: This data item is a pointer to _atom_site.label_seq_id in the
ATOM_SITE category.


* **_pdbx_nonpoly_atom_coordination_sphere_order.label_comp_id**
: This data item is a pointer to _atom_site.comp_id in the ATOM_SITE
category.


* **_pdbx_nonpoly_atom_coordination_sphere_order.label_atom_id**
: The identifier for the target atom to which the feature is assigned.


* **_pdbx_nonpoly_atom_coordination_sphere_order.label_alt_id**
: A place holder to indicate alternate conformation.


* **_pdbx_nonpoly_atom_coordination_sphere_order.auth_asym_id**
: A component of the identifier for the residue at which the
conformation segment begins.

This data item is a pointer to _atom_site.auth_asym_id in the
ATOM_SITE category.


* **_pdbx_nonpoly_atom_coordination_sphere_order.auth_seq_id**
: A component of the identifier for the residue at which the
conformation segment begins.

This data item is a pointer to _atom_site.auth_seq_id in the
ATOM_SITE category.


* **_pdbx_nonpoly_atom_coordination_sphere_order.auth_comp_id**
: A component of the identifier for the residue at which the
conformation segment begins.

This data item is a pointer to _atom_site.auth_comp_id in
the ATOM_SITE category.


* **_pdbx_nonpoly_atom_coordination_sphere_order.auth_atom_id**
: A component of the identifier for partner 1 of the structure
connection.

This data item is a pointer to _atom_site.auth_atom_id in the
ATOM_SITE category.


* **_pdbx_nonpoly_atom_coordination_sphere_order.PDB_ins_code**
: PDB insertion code.


* **_pdbx_nonpoly_atom_coordination_sphere_order.atom_place**
: This data item enumerates the order of the atom in the
coordination sphere, which is the encoding of the 3D
arrangement of the atoms.


* **_pdbx_nonpoly_atom_coordination_sphere_order.symmetry_operation**
: The symmetry operator to apply to the specific atom to
move it into the coordinate spehere.


## pdbx_modification_feature
Data items in the PDBX_MODIFICATION_FEATURE category provides
information about all the protein modifications that have been
modeled in the entry.


* **_pdbx_modification_feature.category**
: The category of protein modification.

    *Enumeration:*

      * Metal coordination
      * ...






