---
title: Aspose.Slides for .NET 15.4.0 Release Notes
type: docs
weight: 70
url: /net/aspose-slides-for-net-15-4-0-release-notes/
---

## **Major Changes**
Major Changes

SLIDESNET-31745 - Connectors layouting
## **Minor Changes**
Minor Changes

SLIDESNET-36224 - Unique IDs for symbol id for pictures is needed when exporting slides with images to HTML

SLIDESNET-35359 - Presentation.GetSlideByID() missing in Aspose.Slides

SLIDESNET-33702 - Saving presentation in different slide view types

SLIDESNET-17922 - Splitting table cells

SLIDESNET-36285 - Implement serialization and deserialization of embedded fonts for PPT

SLIDESNET-35273 - Implement SmartArt customization

SLIDESNET-13794 - Consistency in DocumentProperties
## **Other Improvements and Changes**
# **Other Improvements and Changes**
Bug Fixes

SLIDESNET-36419 - Template Name property missing in Document Properties

SLIDESNET-36392 - SlideCollection.ResetEffectiveFormat throws NullReferenceException

SLIDESNET-36390 - PowerPoint craches on playing presentation with embedded video, 15.5.0

SLIDESNET-36363 - DateTimeInvalid Local format exception is thrown on saving presentation

SLIDESNET-36359 - Slide notes failed to get added in presentation

SLIDESNET-36358 - Strikethrough is appearing thick in generated thumbnail and pdf

SLIDESNET-36357 - Inverse mapping of RotationX and RotationY in Rotation3D Members.

SLIDESNET-36355 - FontHeight changing does not work

SLIDESNET-36350 - PowerPoint shows a repair request when a presentation generated with Aspose.Slides is opened

SLIDESNET-36336 - Issue with Bullets in pptx and ppt

SLIDESNET-36332 - Error Bars are missing in generated thumbnail

SLIDESNET-36322 - Presentation repair message pops on saving the presentation.

SLIDESNET-36316 - Portion format returns wrong font names

SLIDESNET-36311 - Chart labels and legends gets disturbed in generated PDF

SLIDESNET-36310 - Chart labels and legends gets disturbed in saved presentation

SLIDESNET-36309 - Slide background image gets jagged pdf.

SLIDESNET-36308 - Text size is not reduced when TextAutoFitType.Normal is used for slide textframe

SLIDESNET-36307 - Absurd memory usage in GetThumbnail() for simple slide with log scale

SLIDESNET-36306 - Custom document properties are not accessible using Aspose.Slides

SLIDESNET-36299 - Input string was not in the correct format exception on adding HTML to text frame

SLIDESNET-36298 - Missed shapes in generated Html

SLIDESNET-36296 - Null Reference exception on cloning row in side the table

SLIDESNET-36295 - Presentation repair message on saving presentation with video

SLIDESNET-36294 - Wrong logo image rendering in generated thumbnail

SLIDESNET-36284 - Font size for text changed in Aspose.Slides saved presentation

SLIDESNET-36277 - Chart Series Markers and lines are improperly rendered in generated thumbnail

SLIDESNET-36276 - Charts axis labels are improperly rendered in thumbnails

SLIDESNET-36267 - Error on opening PPT file

SLIDESNET-36254 - Pptx exception thrown on accessing presentation

SLIDESNET-36223 - Presentation with WordArt generate corrupt PDF

SLIDESNET-36212 - WordArt effect are lost on text when saving the presentation

SLIDESNET-36106 - Presentation gets corrupt when opened in PowerPoint 2007

SLIDESNET-35602 - Save method required to dynamically pass Save Format

SLIDESNET-35474 - Chart category axis is improperly rendered in generated thumbnail

SLIDESNET-33772 - The presentation size grows after slide cloning

SLIDESNET-33655 - ArgumentException thrown on generating the slide thumbnail in Mono MAC environment

SLIDESNET-32649 - Text converted to image while converting PPT to PPTX

SLIDESNET-12585 - Unsupported Brush Type Exception on PPTX to PDF

SLIDESNET-3681 - Accessing objects on the notes page view
## **Public API Changes**
{{< highlight java >}}

 Public API Changes

Enum OrganizationChartLayoutType has been added

Method IBulletFormat.ApplyDefaultParagraphIndentsShifts has been added

Method IConnector.Reroute has been added

using(Presentation input = new Presentation())

{

IShapeCollection shapes = input.Slides[0].Shapes;

IConnector connector = shapes.AddConnector(ShapeType.BentConnector2, 0, 0, 10, 10);

IAutoShape ellipse = shapes.AddAutoShape(ShapeType.Ellipse, 0, 100, 100, 100);

IAutoShape rectangle = shapes.AddAutoShape(ShapeType.Rectangle, 100, 300, 100, 100);

connector.StartShapeConnectedTo = ellipse;

connector.EndShapeConnectedTo = rectangle;

connector.Reroute();

input.Save("output.pptx", SaveFormat.Pptx);

}

Method IPresentation.GetSlideById has been added

using (Presentation presentation = new Presentation())

{

uint id = presentation.Slides[0].SlideId;

IBaseSlide slide = presentation.GetSlideById(id);

Debug.Assert(presentation.Slides[0] == slide);

}

Property IShape.ConnectionSiteCount has been added

using(Presentation input = new Presentation())

{

IShapeCollection shapes = input.Slides[0].Shapes;

IConnector connector = shapes.AddConnector(ShapeType.BentConnector2, 0, 0, 10, 10);

IAutoShape ellipse = shapes.AddAutoShape(ShapeType.Ellipse, 0, 100, 100, 100);

IAutoShape rectangle = shapes.AddAutoShape(ShapeType.Rectangle, 100, 200, 100, 100);

connector.StartShapeConnectedTo = ellipse;

connector.EndShapeConnectedTo = rectangle;

uint wantedIndex = 6;

if (ellipse.ConnectionSiteCount > wantedIndex){

    connector.StartShapeConnectionSiteIndex = wantedIndex;

  }

input.Save("output.pptx", SaveFormat.Pptx);

}

Property ISmartArt.IsReversed has been added

using (Presentation pres = new Presentation())

{

ISmartArt smart = pres.Slides[0].Shapes.AddSmartArt(10, 10, 400, 300, SmartArtLayoutType.BasicProcess);

smart.IsReversed = true;

pres.Save("out.pptx", Export.SaveFormat.Pptx);

}

Property ISmartArt.Nodes has been added

using (Presentation pres = new Presentation())

{

ISmartArt smart = pres.Slides[0].Shapes.AddSmartArt(10, 10, 400, 300, SmartArtLayoutType.VerticalBulletList);

ISmartArtNode node = smart.Nodes[1]; // select second root node

node.TextFrame.Text = "Second root node";

pres.Save("out.pptx", Export.SaveFormat.Pptx);

}

Property ISmartArtNode.IsHidden has been added

using (Presentation pres = new Presentation())

{

ISmartArt smart = pres.Slides[0].Shapes.AddSmartArt(10, 10, 400, 300, SmartArtLayoutType.RadialCycle);

ISmartArtNode node = smart.AllNodes.AddNode();

bool hidden = node.IsHidden; //returns true

if(hidden){

    //do some actions or notifications

  }

pres.Save("out.pptx", Export.SaveFormat.Pptx);

}

Property ISmartArtNode.OrganizationChartLayout has been added

using (Presentation pres = new Presentation())

{

ISmartArt smart = pres.Slides[0].Shapes.AddSmartArt(10, 10, 400, 300, SmartArtLayoutType.OrganizationChart);

smart.Nodes[0].OrganizationChartLayout = OrganizationChartLayoutType.LeftHanging;

pres.Save("out.pptx", Export.SaveFormat.Pptx);

}


Set method for property ISmartArt.Layout has been added

using (Presentation pres = new Presentation())

{

ISmartArt smart = pres.Slides[0].Shapes.AddSmartArt(10, 10, 400, 300, SmartArtLayoutType.BasicBlockList);

smart.Layout = SmartArtLayoutType.BasicProcess;

pres.Save("out.pptx", Export.SaveFormat.Pptx);

}


Minor API changes

{{< /highlight >}}
