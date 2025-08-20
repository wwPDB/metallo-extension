# Metalloprotein Remediation

## Sections

- [Introduction](#introduction)
- [Scope](#scope)
- [Corrections](#corrections)
- [Enhanced Annotation](#enhanced-annotation)
- [Example Enhanced Annotation in CCD Files](#example-enhanced-annotation-in-ccd-files)
- [Example Enhanced Annotation in Coordinate Files](#example-enhanced-annotation-in-coordinate-files)
- [References](#references)
- [Acknowledgements](#acknowledgements)

## Introduction
Toward the goal of sustaining Core Archives of biostructure data and metadata to promote basic and applied research and education, the wwPDB strives to make biostructure data Findable, Accessible, Interoperable and Reusable (FAIR). Owing to unique properties of metals, standard software and procedures developed for organic compounds do not always provide accurate data on metal-containing compounds, which poses major obstacles for data Reusability. Further, the metalloprotein research community has expressed a need for enhanced metal annotation, which would support Findability and Reusability of metalloprotein data. Based on identification of issues that could lead to widespread error propagation and on feedback from the community, metalloproteins were identified as a target for improvement ("remediation").

To improve accuracy and enhance annotation, a new data model for metalloproteins has been developed in consultation with the metalloprotein research community. In addition to providing valuable feedback, the metalloprotein research community served a crucial role in this remediation by providing tools that enable error correction and support enhanced annotation of metalloproteins.

The PDBx/mmCIF dictionary extensions, examples of PDBx/mmCIF files of remediated data representing various cases, and the corresponding proposed Chemical Component Dictionary definitions are provided here at github https://github.com/wwPDB/metallo-extension for testing and adoption by key stakeholders during the development stage, including the metalloprotein community, refinement software developers, cheminformaticians, and 3D visualization software.

## Scope
For this project, the ~900 metal-containing CCDs (80 metal ions and ~820 polyatomic metal chemical components) will be remediated. The focus of the remediation is on polyatomic metal chemical components, which tend to have more challenges in their definition and representation compared to metal ions. Among entries, the ~13,000 entries containing polyatomic metal chemical components will be remediated. Entries containing metal ions are out of scope.

## Corrections
As a key step of the remediation, Chemical Component Dictionary (CCD) files will be corrected as needed to ensure data accuracy and reusability. The following corrections will be completed:
- Standardization of charge on metals and metal-coordinating atoms.
- Generation of proper ideal coordinates for metal-containing chemical components.
- Splitting or merging metal-containing chemical components where required if: 
  - for splitting, the metal is not part of a standalone coordination compound.
  - for merging, the metal coordination is more complete upon merging two components.
- Corrections of inaccuracies in the definition (such as incorrect bond order or missing hydrogens).
  
Providing such corrections is crucial for mitigating error propagation. For instance, if the PDB provides incorrect ideal coordinates in our CCD, these are then reused in future structures, leading to incorrect geometries in new depositions (see CCD F3S example in Figure 1 below).

<img src="imgs/ideal_example.png" alt="linked_mod" width="600px">

Figure 1: Ideal coordinate updates for CCD F3S. Left, ideal coordinates as currently defined in the CCD, with highly distorted angles. Right, updated ideal coordinates using AceDRG, MetalCoord, and servalcat software, with proper angles being slightly obtuse for S-Fe-S (~105 degrees) and acute for Fe-S-Fe (~75 degrees).

## Enhanced Annotation
Enhanced annotations in the CCD files include:
- For metal ions and polyatomic metal chemical components:
  - Indicating the component type (metal cation or metal-containing ligand).
- For polyatomic metal chemical components only:
  - Adopting metalloprotein community software for metal coordination annotation (coordination number, coordination geometry, and coordination descriptor).
  - Annotation of metal-protein interaction.
  - Flagging metal coordination and metal-pi bonds.

Enhanced annotations in the coordinate files include:
- Adopting metalloprotein community software for metal coordination annotation (coordination number, coordination geometry, and coordination descriptor).
- Annotation of metal-protein interaction.

## Example Enhanced Annotation in CCD Files
### Example of component type
The component type annotation will be included in the chem_comp category as shown in the example below for chemical component HEM.
```
#
_chem_comp.id                      HEM
…
_chem_comp.pdbx_comp_type          "metal-containing ligand"
#
```
### Example of metal coordination annotation
Metal coordination is assessed using community software on a per-atom basis at the instance level, to give a complete picture of all coordination partners (protein, nucleic acid, small molecule, water, etc) and the coordination geometry. The coordination descriptor delineates coordination partners and angles that make up the coordination geometry. In the coordination descriptor, the metal is listed first, followed by each coordinating atom in parentheses. Within curly brackets, all angles that allow reconstruction of the primary metal coordination sphere are listed. When there are multiple possible coordination numbers, coordination geometries, or coordination descriptors (due to different possible coordination partners), the different options will be annotated. Annotation will be populated in the pdbx_chem_comp_atom_feature category as shown in the example below for chemical component 1PT. 
```
# 
loop_
_pdbx_chem_comp_atom_coordination.geometry_id 
_pdbx_chem_comp_atom_coordination.comp_id 
_pdbx_chem_comp_atom_coordination.atom_id 
_pdbx_chem_comp_atom_coordination.number 
_pdbx_chem_comp_atom_coordination.geometry 
_pdbx_chem_comp_atom_coordination.geometry_generic 
_pdbx_chem_comp_atom_coordination.provenance 
1 1PT PT 4 'square plane' 'square planar' FindGeo    
1 1PT PT 4 square-planar  'square planar' MetalCoord 
# 
loop_
_pdbx_chem_comp_atom_coordination_sphere.id 
_pdbx_chem_comp_atom_coordination_sphere.geometry_id 
_pdbx_chem_comp_atom_coordination_sphere.comp_id 
_pdbx_chem_comp_atom_coordination_sphere.atom_id 
_pdbx_chem_comp_atom_coordination_sphere.descriptor 
_pdbx_chem_comp_atom_coordination_sphere.provenance 
1 1 1PT PT 'Pt(N)(N)(N)(N){NPtN<90>,NPtN<180>,NPtN<90>,NPtN<90>,NPtN<180>,NPtN<90>}' PDB 
2 1 1PT PT 'Pt(N)(N)(N)(O){NPtN<90>,NPtN<180>,NPtO<90>,NPtN<90>,NPtO<180>,NPtO<90>}' PDB 
3 1 1PT PT 'Pt(N)(N)(O)(O){NPtN<90>,NPtO<180>,NPtO<90>,NPtO<90>,NPtO<180>,OPtO<90>}' PDB 
4 1 1PT PT 'Pt(N)(N)(O)(S){NPtN<90>,NPtO<180>,NPtS<90>,NPtO<90>,NPtS<180>,OPtS<90>}' PDB 
# 
```
### Example of protein-metal interaction
Metal-protein interactions will be annotated in the pdbx_chem_comp_pcm category as shown in the example below for chemical component SF4.
```
#
loop_
_pdbx_chem_comp_pcm.pcm_id                                       
_pdbx_chem_comp_pcm.comp_id                          
_pdbx_chem_comp_pcm.modified_residue_id
_pdbx_chem_comp_pcm.type                                            
_pdbx_chem_comp_pcm.category                                     
_pdbx_chem_comp_pcm.position                           
_pdbx_chem_comp_pcm.polypeptide_position
_pdbx_chem_comp_pcm.comp_id_linking_atom
_pdbx_chem_comp_pcm.modified_residue_id_linking_atom
_pdbx_chem_comp_pcm.uniprot_specific_ptm_accession
_pdbx_chem_comp_pcm.uniprot_generic_ptm_accession
1  SF4 ASP None "Metal coordination" "Amino-acid side chain" "Any position" "FE2" "OD1" ? ?
2  SF4 ASP None "Metal coordination" "Amino-acid side chain" "Any position" "FE2" "OD2" ? ?
3  SF4 ASP None "Metal coordination" "Amino-acid side chain" "Any position" "FE3" "OD1" ? ?
4  SF4 ASP None "Metal coordination" "Amino-acid side chain" "Any position" "FE3" "OD2" ? ?
5  SF4 ASP None "Metal coordination" "Amino-acid side chain" "Any position" "FE4" "OD1" ? ?
6  SF4 ASP None "Metal coordination" "Amino-acid side chain" "Any position" "FE4" "OD2" ? ?
7  SF4 CYS None "Metal coordination" "Amino-acid side chain" "Any position" "FE1" "SG"  ? ?
8  SF4 CYS None "Metal coordination" "Amino-acid side chain" "Any position" "FE2" "SG"  ? ?
9  SF4 CYS None "Metal coordination" "Amino-acid side chain" "Any position" "FE3" "SG"  ? ?
10 SF4 CYS None "Metal coordination" "Amino-acid side chain" "Any position" "FE4" "SG"  ? ?
11 SF4 GLN None "Metal coordination" "Amino-acid side chain" "Any position" "FE1" "NE2" ? ?
12 SF4 GLN None "Metal coordination" "Amino-acid side chain" "Any position" "FE1" "OE1" ? ?
13 SF4 GLN None "Metal coordination" "Amino-acid side chain" "Any position" "FE3" "OE1" ? ?
15 SF4 GLU None "Metal coordination" "Amino-acid side chain" "Any position" "FE2" "OE1" ? ?
16 SF4 GLU None "Metal coordination" "Amino-acid side chain" "Any position" "FE3" "OE1" ? ?
17 SF4 GLU None "Metal coordination" "Amino-acid side chain" "Any position" "FE3" "OE2" ? ?
18 SF4 GLU None "Metal coordination" "Amino-acid side chain" "Any position" "FE4" "OE2" ? ?
19 SF4 HIS None "Metal coordination" "Amino-acid side chain" "Any position" "FE1" "ND1" ? ?
20 SF4 HIS None "Metal coordination" "Amino-acid side chain" "Any position" "FE1" "NE2" ? ?
21 SF4 HIS None "Metal coordination" "Amino-acid side chain" "Any position" "FE2" "ND1" ? ?
22 SF4 HIS None "Metal coordination" "Amino-acid side chain" "Any position" "FE2" "NE2" ? ?
23 SF4 HIS None "Metal coordination" "Amino-acid side chain" "Any position" "FE3" "ND1" ? ?
24 SF4 HIS None "Metal coordination" "Amino-acid side chain" "Any position" "FE3" "NE2" ? ?
25 SF4 HIS None "Metal coordination" "Amino-acid side chain" "Any position" "FE4" "ND1" ? ?
26 SF4 HIS None "Metal coordination" "Amino-acid side chain" "Any position" "FE4" "NE2" ? ?
27 SF4 SER None "Metal coordination" "Amino-acid side chain" "Any position" "FE4" "OG"  ? ?
28 SF4 TYR None "Metal coordination" "Amino-acid side chain" "Any position" "FE1" "OH"  ? ?
29 SF4 TYR None "Metal coordination" "Amino-acid side chain" "Any position" "FE3" "OH"  ? ?
#
```
### Examples of metal coordination and metal-pi bond flags
For metal coordination and metal-pi bonds, new flags will be introduced in the chem_comp_bond category. The metal coordination flag will be used for all metal-nonmetal bonds, whereas the metal-pi bond flag will be used only when the bond between a metal and a pi system. See examples below for SF4 and RUC.
```
#
loop_
_chem_comp_bond.comp_id
_chem_comp_bond.atom_id_1
_chem_comp_bond.atom_id_2
_chem_comp_bond.value_order
_chem_comp_bond.pdbx_aromatic_flag
_chem_comp_bond.pdbx_stereo_config
_chem_comp_bond.pdbx_metal_coordination_flag
_chem_comp_bond.pdbx_metal_pi_flag
_chem_comp_bond.pdbx_ordinal
SF4 FE1 S2 SING N N Y N 1 
SF4 FE1 S3 SING N N Y N 2 
SF4 FE1 S4 SING N N Y N 3 
SF4 FE2 S1 SING N N Y N 4 
SF4 FE2 S3 SING N N Y N 5 
SF4 FE2 S4 SING N N Y N 6 
SF4 FE3 S1 SING N N Y N 7 
SF4 FE3 S2 SING N N Y N 8 
SF4 FE3 S4 SING N N Y N 9 
SF4 FE4 S1 SING N N Y N 10
SF4 FE4 S2 SING N N Y N 11
SF4 FE4 S3 SING N N Y N 12
#
loop_
_chem_comp_bond.comp_id
_chem_comp_bond.atom_id_1
_chem_comp_bond.atom_id_2
_chem_comp_bond.value_order
_chem_comp_bond.pdbx_aromatic_flag
_chem_comp_bond.pdbx_stereo_config
_chem_comp_bond.pdbx_metal_coordination_flag
_chem_comp_bond.pdbx_metal_pi_flag
_chem_comp_bond.pdbx_ordinal
RUC C29  C30 DOUB N N N N 1 
RUC C29  C28 SING N N N N 2 
RUC C30  C31 SING N N N N 3 
RUC C31  C26 DOUB N N N N 4 
RUC C26  C27 SING N N N N 5 
RUC C27  C28 DOUB N N N N 6 
RUC C29  H29 SING N N N N 7 
RUC C30  H30 SING N N N N 8 
RUC C31  H31 SING N N N N 9 
RUC C26  H26 SING N N N N 10
RUC C27  H27 SING N N N N 11
RUC C28  H28 SING N N N N 12
RUC RU11 C29 SING N N Y Y 13
RUC RU11 C30 SING N N Y Y 14
RUC RU11 C31 SING N N Y Y 15
RUC RU11 C26 SING N N Y Y 16
RUC RU11 C27 SING N N Y Y 17
RUC RU11 C28 SING N N Y Y 18
#
```
## Example Enhanced Annotation in Coordinate Files
### Example of metal coordination annotation
For the coordinate files, metal coordination will be assessed using community software and compared with the coordination annotation in the CCD (if available) to determine if the coordination geometry is 'expected' (matching with the CCD) or 'unexpected' (not matching with the CCD). See example below for 1pg9, an entry containing chemical component 1PT.
```
# 
loop_
_pdbx_nonpoly_atom_coordination.geometry_id 
_pdbx_nonpoly_atom_coordination.label_asym_id 
_pdbx_nonpoly_atom_coordination.comp_id 
_pdbx_nonpoly_atom_coordination.atom_id
_pdbx_nonpoly_atom_coordination.alt_id
_pdbx_nonpoly_atom_coordination.number 
_pdbx_nonpoly_atom_coordination.geometry 
_pdbx_nonpoly_atom_coordination.geometry_generic 
_pdbx_nonpoly_atom_coordination.provenance 
_pdbx_nonpoly_atom_coordination.assessment 
1 C 1PT PT ? 4 'square plane (regular)' 'square planar' FindGeo    Expected 
1 C 1PT PT ? 4 square-planar            'square planar' MetalCoord Expected 
# 
_pdbx_nonpoly_atom_coordination_sphere.geometry_id     1 
_pdbx_nonpoly_atom_coordination_sphere.label_asym_id   C 
_pdbx_nonpoly_atom_coordination_sphere.comp_id         1PT 
_pdbx_nonpoly_atom_coordination_sphere.atom_id         PT 
_pdbx_nonpoly_atom_coordination_sphere.alt_id          ? 
_pdbx_nonpoly_atom_coordination_sphere.descriptor      'Pt(N)(N)(N)(N){NPtN<90>,NPtN<180>,NPtN<90>,NPtN<90>,NPtN<180>,NPtN<90>}' 
_pdbx_nonpoly_atom_coordination_sphere.provenance      PDB 
# 
```
### Example of protein-metal interaction
In coordinate files, metal-protein interactions will be annotated in the pdbx_modification_feature category as shown in the example below for chemical component 5wqq, an entry containing chemical component SF4.
```
#
loop_
_pdbx_modification_feature.ordinal
_pdbx_modification_feature.label_comp_id
_pdbx_modification_feature.label_asym_id
_pdbx_modification_feature.label_seq_id
_pdbx_modification_feature.label_alt_id
_pdbx_modification_feature.modified_residue_label_comp_id
_pdbx_modification_feature.modified_residue_label_asym_id
_pdbx_modification_feature.modified_residue_label_seq_id
_pdbx_modification_feature.modified_residue_label_alt_id
_pdbx_modification_feature.auth_comp_id
_pdbx_modification_feature.auth_asym_id
_pdbx_modification_feature.auth_seq_id
_pdbx_modification_feature.PDB_ins_code
_pdbx_modification_feature.symmetry
_pdbx_modification_feature.modified_residue_auth_comp_id
_pdbx_modification_feature.modified_residue_auth_asym_id
_pdbx_modification_feature.modified_residue_auth_seq_id
_pdbx_modification_feature.modified_residue_PDB_ins_code
_pdbx_modification_feature.modified_residue_symmetry
_pdbx_modification_feature.comp_id_linking_atom
_pdbx_modification_feature.modified_residue_id_linking_atom
_pdbx_modification_feature.modified_residue_id
_pdbx_modification_feature.ref_pcm_id
_pdbx_modification_feature.ref_comp_id
_pdbx_modification_feature.type
_pdbx_modification_feature.category
1 SF4 B . ? CYS A 43 ? SF4 A 101 ? 1_555 CYS A 43 ? 1_555 FE1 SG CYS 7  SF4 None 'Metal coordination'
2 SF4 B . ? CYS A 46 ? SF4 A 101 ? 1_555 CYS A 46 ? 1_555 FE2 SG CYS 8  SF4 None 'Metal coordination'
3 SF4 B . ? CYS A 61 ? SF4 A 101 ? 1_555 CYS A 61 ? 1_555 FE3 SG CYS 9  SF4 None 'Metal coordination'
4 SF4 B . ? CYS A 75 ? SF4 A 101 ? 1_555 CYS A 75 ? 1_555 FE4 SG CYS 10 SF4 None 'Metal coordination'
#
```
## References
[FindGeo](https://metalweb.cerm.unifi.it/tools/findgeo_help/): Andreini C, Cavallaro G, Lorenzini S. FindGeo: a tool for determining metal coordination geometry. Bioinformatics 2012, 28(12), 1658-1660.

[MetalCoord](https://github.com/Lekaveh/MetalCoordAnalysis): Babai, KH, Long, F, Malý M, Yamashita K, Murshudov GN. Improving macromolecular structure refinement with metal-coordination restraints. Acta Crystallogr D Biol Crystallogr 2024, D80, 821-833.

## Acknowledgements
The metalloprotein remediation project is a wwPDB collaborative project that is carried out principally by [RCSB PDB](https://rcsb.org/) at Rutgers, The State University of New Jersey and is funded by the U.S. National Science Foundation (DBI-2321666), the US Department of Energy (DE-SC0019749), and the National Cancer Institute, National Institute of Allergy and Infectious Diseases, and National Institute of General Medical Sciences of the National Institutes of Health under grant R01GM157729.
