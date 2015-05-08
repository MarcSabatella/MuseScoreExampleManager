# MuseScoreExampleManager
***LibreOffice / OpenOffice extension to manage [MuseScore](https://musescore.org/) sheet music examples within text documents.***

The extension runs equally well on LibreOffice (LO) and Apache OpenOffice (AOO).
Where you see OpenOffice (OO) written in this guide you may assume it applies to both.

- The latest stable version is available from the [LibreOffice Extension Centre](http://extensions.libreoffice.org/extension-center/musescore-example-manager)
  , along with past releases.
- Development is done through [GitHub](https://github.com/MarcSabatella/MuseScoreExampleManager).
  Code contributions are welcome via [Pull Requests](https://help.github.com/articles/using-pull-requests/).

For the extension to function, full copies of [MuseScore](https://musescore.org/) and
[ImageMagick](http://www.imagemagick.org/) must be present on the system. The extension
works by running MuseScore in the background to generate PNG images from sheet music (.mscz)
files. These PNG images are trimmed by ImageMagick and inserted into the OpenOffice
document. It is easy to update the images later if the original score is modified.

## Usage: inserting and updating sheet music images

From within OpenOffice, put the cursor where you want a sheet music example to appear. Go to
*"Insert -> MuseScore Example"* and select an MSCZ file.  A graphic representation of
the example (with excess whitespace automatically trimmed) will be generated and inserted
into your document with a link to the original MSCZ file.  Ctrl-click the example to edit
it further in MuseScore.  After editing and saving the example in MuseScore, you can select
the graphic in OpenOffice and press the MuseScore button again to update it.

## Installation: adding the extension to LibreOffice / Apache OpenOffice

Before commencing, ensure you have a working copy of [MuseScore](https://musescore.org/) on your computer.

1. Download the [MuseScoreExampleManager](http://extensions.libreoffice.org/extension-center/musescore-example-manager)
   extension package (*.oxt* file) onto your computer. It will be called _"musescore-X.Y.Z.oxt"_
   where *X.Y.Z* corresponds to the target MuseScore version (e.g. 2.0.1).
2. Save and close any open OpenOffice documents.
3. Open a new Writer document.
4. Go to _Tools -> Extension Manager... -> Add..._ and locate the *.oxt* file.
5. Restart OpenOffice.

## First Run: locating dependencies

The MuseScoreExampleManager extension relies on other programs to process the sheet
music and images in the background. The first time you run the extension you will be
asked for the location of these programs in the form of a file path. The file path
must include both the filename of the executable and the installation directory.

### Locating MuseScore

The first time you run the extension within OpenOffice, you will be prompted
for the file path to the MuseScore excecuteable. The default paths are:

- __Windows:__ _"C:\Program Files (x86)\MuseScore X\bin\MuseScore.exe"_ (*X* is version number).
- __Mac:__ _"/Applications/MuseScore X.app/Contents/MacOS/mscore"_ (*X* is version number).
- __Linux:__ _"/usr/bin/mscore"_ (or the output of the Terminal command `which mscore`).

Note: if you have multiple copies of MuseScore installed then make sure
you give the path to the correct version.

### Locating "mogrify" (ImageMagick)

On first run you will also be prompted for the path to the "mogrify"
command provided by the [ImageMagick](http://www.imagemagick.org/) program.
This is used to trim excess whitespace from the edges of sheet music images.

## Development: adding new features to the MuseScoreExampleManager extension

### Source code

You can open up the extension package OXT file in any regular archival
program (e.g. WinZip) to view the source code and make small changes to
your personal copy. If you are making larger changes, or if you want to
share your changes with the world, then you must use GitHub (see below).

### Compiling and Packaging

The file _"musescore.odt"_ contains OpenOffice macros that perform the whole packaging process for you
(it's a copy of the [OpenOffice Extension Compiler](https://wiki.openoffice.org/wiki/Extensions_Packager#Extension_Compiler)).
It analyses the code and generates some XML manifest documents which are packaged up with the source code
inside a ZIP archive. The archive is given the OXT extension and it is this that is added to OpenOffice.

To "compile" (package) the source code into an OXT extension file:

1. Delete any temporary autosave files in the package directory (they
   may be hidden) to avoid including them in the final package.
2. Open the Writer document _"musescore.odt"_ and run the macro on page 8.

You may have to give permission for the macro to run. It will also require a copy
of the [Java Runtime Environment](https://www.java.com) (JRE) to be installed on
your computer. Alternatively, the [OpenJDK](http://openjdk.java.net/) is perfectly
adequate, and can be found in the default repository of many Linux distributions.

### Contributing via GitHub

Code contributions are welcome and should be submitted in the form of Pull Requests.
Detailed instructions are available elsewhere.

Unlike most projects on GitHub, this one contains a copy of the compiled program as well
as the raw source code. Make sure you repackage **before** you submit the Pull Request.
