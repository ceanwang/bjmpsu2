## A tool to convert su2 file into GMSH's pos file


## 1 Convert

Under DOS terminal, run:

mpsu2 mesh_NACA0012_inv

This will convert mesh_NACA0012_inv.su2 file. No need to input su2 extension name. This will generate mesh_NACA0012_inv.pos file and it could be viewed with GMSH.

It also generate a mesh_NACA0012_inv.mesh file. It is a input file for mesh partition progam mpmetis.exe.


## 2 mesh partition

Here we use 4 partitions for example:

Under dos terminal，run：

mpmetis mesh_NACA0012_inv.mesh 4

mpmetis will input from mesh_NACA0012_inv.mesh file. Must specify .mesh extension name.

The parameter 4 at the end specify the number of partitions we wanted.

This will  generate mesh_NACA0012_inv.mesh.epart.4 and mesh_NACA0012_inv.mesh.npart.4 files. The epart file tells which partition an element is belong to. The npart  tells which partition a node is belong to.


## 3 Plot partitioned mesh

Under dos terminal，run：

mpsu2 mesh_NACA0012_inv 4

This command has a extra parameter 4 at the end which specify the number of partitions.

This will generate mesh_NACA0012_inv.pos file，view with gmsh.

## Notice：

mpsu2.exe currently does not support memo line started with % in a su2 file.

