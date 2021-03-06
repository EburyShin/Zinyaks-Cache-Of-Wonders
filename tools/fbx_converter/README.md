# FBX Converter

These files are used to convert an FBX format file into xml-based files that can be used in the crunch process to bring new assets into SR4.  In addition to this python script, users will need the following external tools:

* [Python 2.6](http://www.python.org/getit/)
* [Wx Python](http://www.wxpython.org/download.php)
* [FBX Python SDK 2014 for Python 2.6](http://usa.autodesk.com/adsk/servlet/pc/item?iteID=123112&id=10775847)

Please make sure that you download the appropriate version of wxPython for the Python distribution that is installed on your machine.

# Creating your Mesh

## Skinning and Bones

Your mesh must have a skin deformer with skin weighted bones to be properly
converted.

There are attributes which I will have to outline later for ordering the bones
but for now a default hierarchy with a **single** parent root node should be
handled properly.



![](https://voligitlab01.dsvolition.com/uploads/note/attachment/1/image012.png)



## Attachment Tags

Weapons and Characters have dummy objects used to define fx or attachment
locations. These dummy or null objects **must** be children of bones found in
the skin clusters. The tags must either have a “p_tag_name” custom attribute
or a “$prop-” name prefix. We can update the prefix name to better suit DCC
applications that don’t care for special characters in the name. Weapons have
the following tags.

_Must Have_

“weapon_handle” – where it attaches to the hand of a character

“secondary_handle” – where the offhand will ik attach to the weapon

“muzzle_flash” – where the muzzle flash fx will play from



_Optional Per Weapon_

“attach” – attach to character position ( On the back of a character etc )

“gunmag_handle” – clip attachment position

“vfx(1-x)”

“shell_eject”

“shell_eject(1-x)”

“weapon_center”

“weapon_impact” – hit location of the weapon when used in melee attach

“weapon_impact(1-x)”



## Materials & Textures

You should place all of your textures in the same folder location you plan to
export the FBX file to. When the material is written out to our format the
textures assigned to specific material attributes in the DCC app will get
slotted as follows. So make sure the appropriate texture is assigned to the
proper material attribute.



![](https://voligitlab01.dsvolition.com/uploads/note/attachment/2/image013.jpg)



Sphere maps are shaderball textures used for a custom ShaderBall shader. More
details should come on setting this material up later.

**Start with assigning Simple1 or Simple3 in the FBX Converter**



## 3dsmax Units Setup

If you are working in 3dsmax you should set your units to the following.

![](https://voligitlab01.dsvolition.com/uploads/note/attachment/3/image014.jpg)



## Maya Units Setup

If you are working in Maya you should adjust your settings to the following.

![](https://voligitlab01.dsvolition.com/uploads/note/attachment/4/image005.png)





# Exporting

Follow the FBX export templates provided here to export your mesh from the DCC
application. The main settings to be aware of are the “Units” and “Up Axis”.



### Specifically

Units = Inches

Up Axis = Y-up



**MAYA FBX EXPORT SETTINGS**

![](https://voligitlab01.dsvolition.com/uploads/note/attachment/5/image015.jpg)****

** **

**3dsMax FBX EXPORT SETTINGS**

![](https://voligitlab01.dsvolition.com/uploads/note/attachment/6/image016.jpg)** **







**Using the FBX Converter**

1\. Import FBX file

2\. The main skinned mesh should be selected by default, if not select that to
get the proper results

3\. Double-click and assign SR shader to each material found on the mesh

4\. Hit the check button for each file type to convert/create.

·         The output file locations are automatically set to the source FBX
file location. This should probably not change.

5\. Hit Convert

·         Additional files will default to being generated in the same
location as the source FBX file.



![](https://voligitlab01.dsvolition.com/uploads/note/attachment/7/image017.jpg)

**Thomas Rausch Appended Info** 
The following is just some further clarification on the required installers. Here is which installers I downloaded specficially. 
    
* Python 2.6.6 is the latest version of Python 2.6 with a Windows installer so that’s the one I downloaded from this page: 
http://www.python.org/getit/releases/2.6.6/  
I downloaded the 64 bit version named “Windows X86-64 MSI Installer (2.6.6) [1] (sig)”

* Next get Wx Python from: http://www.wxpython.org/download.php
  Grab the one named “wxPython3.0-win64-py26”

* Next you need to get the FBX 2014.1 SDK from Autodesk.  Autodesk’s site doesn’t like to be linked to, some cookie related thing.  So go ahead and go to http://www.autodesk.com/products/fbx/overview
 1. Scroll down to “Download free* FBX software development kits (SDKs)”.   
 2. Click that, once on that page scroll down to “SDK Archive”.  
 3. Click that, once on that page click “FBX 2014.1 SDK”
 4. Download the Windows Installer under the “Python Binding” heading. 

* Install all 3 programs, with Python 2.6 being installed first. 
 Finally you need to copy some files from the FBX 2014.1 SDK directory to your Python 2.6 directory. This link from Autodesk explains it pretty well: http://download.autodesk.com/us/fbx/20112/FBX_SDK_HELP/index.html?url=WS73099cc142f48755-751de9951262947c01c-6dc7.htm,topicNumber=d0e8430