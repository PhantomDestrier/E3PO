# Introduction
E3PO is an **O**pen **P**latform for **3**60° video streaming simulation and **E**valuation. E3PO is designed to support the simulation of a variety of 360° video streaming approaches that have been proposed so far, including projection based, tile based, or transcoding based. Particularly, E3PO allows users to convert 360° video into standard or customized projections, segment video into equal or adaptive sizes, implement customized motion prediction algorithms, apply different streaming strategies, and evaluate using any user-specific metrics. Most importantly, E3PO generates the actual visual sequences that will display on the user screen for each simulation. 

Therefore, E3PO provides a perfect solution to objectively compare the performance of different 360° video streaming approaches, using the same video content and same motion trace.



# Framework
The framework of E3PO is illustrated as the following figure, which consists of three principal modules, i.e., the ***video pre-processor***, the ***streaming simulator*** and the ***system evaluator***.

To simulate a streaming approach, the ***video pre-processor*** first segments the 360° panoramic video into small video tile chunks according to users’ specific projection and tiling parameters. Then the ***streaming simulator*** reads the provided head motion trace, and simulates the detailed streaming actions which include when and which video chunk is transmitted. Last, the ***system evaluator*** synthesizes the video sequence that is displayed on the user screen and calculates various metrics.

![](/docs/Framework.jpg "e3po_framework")



# Quick Start

## Code & Dataset
1. Download E3PO code
```
git clone https://github.com/bytedance/E3PO.git
```

2. Video Source<br>
Prepare a 360° video (which is not included in E3PO repo), rename and place it at /e3po/source/video/[sample].mp4. Note that the file name and video attributions should match the configurations listed in e3po/e3po.yml.  We have provided a sample video for particpants of 2024 MMSys Grand Challenge.


3. Motion Trace<br>
Prepare a motion trace file and place it at /e3po/source/motion_trace/[motion_trace].log. Note that E3PO has provided a sample file. If you want to use a different one, you can generate one similarly to that from [360VidStr](https://github.com/360VidStr/A-large-dataset-of-360-video-user-behaviour/blob/main/AggregatedDataset/7.txt).

## ERP Method
ERP method is used to map a spherical 360-degree video onto a 2D rectangular plane.
1. Mapping Spherical Coordinates: ERP involves projecting spherical coordinates (latitude and longitude) directly onto a rectangular grid, creating a 2D equirectangular image.
2. Uniform Angular Steps: Both polar (vertical) and azimuthal (horizontal) angles are sampled uniformly, maintaining consistent angular steps.
3. Aspect Ratio: The resulting image has an aspect ratio of 2:1, as the full 360-degree longitude is mapped to the width and 180-degree latitude to the height.
4. Pixel Density: This method inherently causes pixel density to be non-uniform, with higher density near the poles and lower density near the equator.
