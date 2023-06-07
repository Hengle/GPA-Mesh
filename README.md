# GPA-Mesh

## Extraction of models with uv from Intel GPA

This is a very tiny cmd tool (.obj model UV insertion tool), with only about a hundred lines of code.

The model extracted from GPA does not come with UV information, we can extract UV information from VBV csv file to insert into the .obj model.

How to use:

Need to use cmd call: command : [geometry.obj path] [vbv.csv path] [column name] [output path]

- geometry.obj path
    
    It should be the obj model you exported from GPA

- vbv.csv path

    It should be the VBV file (.csv) you exported from GPA, usually there will be more than one VBV in one DrawCall of GPA, please pay attention to which VBV file the UV information exists, we need to use the VBV with UV information.

- column name

    Usually there is no specific name for UV in VBV, please select a column of data in VBV as UV information, usually this column will be called TEXCOORD / TEXCOORD0 / TEXCOORD* / float2, the value of this column is characterized by only x and y values, and are between 0 and 1, cut are floating point numbers, you need to screen the name of this UV column yourself What is then passed in, the name can be seen in the first line of the data displayed in GPA by clicking VBV, the general layout format is index columnName1 columnName2 ...

- output path

    Path to export model

Example (in cmd):
```
gmesh inputmesh.obj VBV.csv TEXCOORD inputmesh.obj
```

