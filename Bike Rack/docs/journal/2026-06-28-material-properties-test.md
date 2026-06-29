# 2026-06-28-material-properties-test.md

## Updates and Issues

<br>
Test Model Description: <br>
Number of Parts:- 3 <br>
Materials:- PVC-Generic (Plank01), ABS-Generic (Plank02), Aluminum-Generic  (Dowell)
<br>

<br>
Mesh Parameters
Element Dimensions: 3D <br>
Element Order: 2nd <br>
Maximum Size: 0.5 in <br>
Minimum Size: 0.0 in 
<br>

<br>
Preparation finished <br>
Start process... <br>
Warning : Volume mesh: worst distortion = -0.316028 (avg = 0.99022, 1 elements with jac. < 0) <br>
Warning : ------------------------------ <br>
Warning : Mesh generation error summary <br>
Warning :     1 warning <br>
Warning :     0 errors <br>
Warning : Check the full log for details <br>
Warning : ------------------------------ <br>
Process finished <br>
Time: 2.6 s
<br>

<br>
Mesh Parameters <br>
Element Dimensions: 3D <br>
Element Order: 2nd <br>
Maximum Size: 0.3 in <br>
Minimum Size: 0.0 in
<br>

<br>
Prepare process... <br>
Preparation finished <br>
Start process... <br>
Process finished <br>
Time: 5.8 s 
<br>

<br>
Compounding the assembly seems to be the right move over boolean union, but tolerances are now an issue. <br>

Since separate parts are needed for assigned material properties, the assembly cannot be fused together. Fusing them together (union) would be much easier, as this simplifies the mesh but reduces the complexity allowed assembly/simulation-wise. <br>

More on the meshing of compounds: where my issues of tolerances come in is with the decision and understanding of how the mesh/elements will react to part geometries coming into exact contact (0.0 gap). <br>

The reason for wanting to gain a greater understanding of this is because it could help immensely in the simulation of the bike rack assembly/simulation. <br>

With only 3 parts, 3 materials, and 2 constraints (fixed & force), this should be a relatively simple model to run analysis on. Certain problems that have arisen are jacobena value <= 0 (Gmsh), tetrahedron = 0 (Netgen), and general FEA workflow troubles. <br>


<br>
Bellow is from CalculiX trying to run, but instead throwing a related error to getting elements for solving. <br>
21:19:27  <br>
21:19:27  Check prerequisites... <br>
21:19:27  <br>
21:19:27  Get mesh data for constraints, materials and element geometry... <br>
21:19:27  Materials <br>
21:19:27  Constraint: MaterialSolid --> We have mesh groups. We will search for appropriate group data. <br>
21:19:27  Constraint: MaterialSolid001 --> We have mesh groups. We will search for appropriate group data. <br>
21:19:27  Constraint: MaterialSolid002 --> We have mesh groups. We will search for appropriate group data. <br>
21:19:27  Count finite elements as sum of constraints:   0 <br>
21:19:27  Count finite elements of the finite element mesh: 24608 <br>
21:19:27  ERROR: femelement_table != count_femelements <br>
21:19:27  Error in get_femelement_sets_from_group_data -- > femelements_count_ok() failed! <br>
21:19:27  False <br>
21:19:27  Constraint: MaterialSolid --> We're going to search in the mesh for the element ID's. <br>
21:19:27      ReferenceShape ... Type: Solid, Object name: Compound, Object label: Compound, Element name: Solid1 <br>
21:19:27  binary search: get_femelements_by_femnodes_bin <br>
21:19:27  len femnodes_ele_table: 41850 <br>
21:19:27  found Volumes: 15291 <br>
21:19:27  Constraint: MaterialSolid001 --> We're going to search in the mesh for the element ID's. <br>
21:19:27      ReferenceShape ... Type: Solid, Object name: Compound, Object label: Compound, Element name: Solid3 <br>
21:19:27  binary search: get_femelements_by_femnodes_bin <br>
21:19:27  len femnodes_ele_table: 41850 <br>
21:19:27  found Volumes: 8228 <br>
21:19:27  Constraint: MaterialSolid002 --> We're going to search in the mesh for the element ID's. <br>
21:19:27      ReferenceShape ... Type: Solid, Object name: Compound, Object label: Compound, Element name: Solid2 <br>
21:19:27  binary search: get_femelements_by_femnodes_bin <br>
21:19:27  len femnodes_ele_table: 41850 <br>
21:19:27  found Volumes: 1089 <br>
21:19:27  Count finite elements as sum of constraints:   24608 <br>
21:19:27  Count finite elements of the finite element mesh: 24608 <br>
21:19:27  ConstraintFixed: <br>
21:19:27      Type: Fem::ConstraintFixed, Name: ConstraintFixed <br>
21:19:27      ReferenceShape ... Type: Face, Object name: Compound, Object label: Compound, Element name: Face2 <br>
21:19:27  ConstraintForce: <br>
21:19:27      Type: Fem::ConstraintForce, Name: ConstraintForce <br>
21:19:27      ReferenceShape ... Type: Face, Object name: Compound, Object label: Compound, Element name: Face26 <br>
21:19:27  Getting mesh data time: 200.469 seconds. <br>
21:19:27  <br>
21:19:27  CalculiX solver input writing... <br>
21:19:27  Input file:C:\Users\cmcka\AppData\Local\Temp\fcfem_zk5iif48\FEMMeshGmsh.inp <br>
21:19:27  One monster input file. <br>
21:19:27  Writing time CalculiX input file: 0.797 seconds. <br>
<br>

---

<p align="center">
  <img src="../images/renders/materialsTest-assemblyGIF-quality.gif" width="700">
</p>

<p align="center">
  <img src="../images/renders/materialsTest.png" width="700">
</p>

<p align="center">
  <img src="../images/renders/materialsTest-mesh.png" width="700">
</p>
