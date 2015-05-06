# About ARToolkit

ARToolKit is software that lets programmers easily develop Augmented Reality applications. Augmented Reality (AR) is the embedding of computer generated content into the natural environment, and has many potential applications in entertainment, media, advertising, industry, and academic research.

One of the most difficult parts of developing an augmented reality application is precisely calculating the user's viewpoint in real time so that the virtual images are exactly aligned with real world objects. ARToolKit uses computer vision techniques to calculate the real camera position and orientation relative to square shapes or flat textured surfaces, allowing the programmer to overlay virtual objects. The fast, precise tracking provided by ARToolKit has enabled the rapid development of thousands of new and interesting AR applications.

The documentation contains a complete description of the ARToolKit library, how to install it, and how to use its functionality in AR applications. Several simple sample applications are provided with ARToolKit to enable the programmer to get started immediately. ARToolKit includes the tracking libraries and complete source code for these libraries enabling programming to port the code to a variety of platforms or customize it for their own applications.

ARToolKit is multi-platform, running on the Windows, Mac OS X, Linux, iOS and Android operating systems. The functionality of each version of the toolkit is the same, but the performance may vary depending on the different hardware configurations. ARToolKit can be easily ported to other new and experimental platforms.

ARToolKit supports both video and optical see-through augmented reality. Video see-through AR is where virtual images are overlaid on live video of the real world. The alternative is optical see-through augmented reality, where computer graphics are overlaid directly on a view of the real world. Optical see-through augmented reality typically requires a see-through head mounted display and has more complicated camera calibration and registration requirements.

## ARToolKit Professional v4.1 Features

- Tracking of fiducial markers (black and white marker squares with user-definable patterns) in video streams, and compositing of computer-generated content to produce video-overlay or see-through augmented reality objects.
- Video stream acquisition from a large variety of cameras and video sources, including professional IIDC firewire cameras, consumer level USB web cameras, digital video, and a variety of specialist video capture sources.
- Multiple video streams can be captured simultaneously, and dynamically switched, or multiplexed for stereo and / or multi-user/single-CPU AR applications.
- Acquisition from pre-recorded and live-streamed remote sources, including QuickTime, Video for Windows, RTSP streaming, MPEG4 and 3GPP streams.
- Integration with OpenGL for production of AR content and high-speed video pass-through, plus rendering of high-level graphical content and animations in Virtual Reality Modelling Language (VRML) v2 and X3D format.
- Support for a variety of lens models and optical calibration techniques, including ARToolKit v2 lens models and ARToolKit v4 enhanced lens models. Calibration utilities allow users to accurately and automatically calculate lens characteristics of the cameras in use.
- Modern object-oriented API design allows multiple tracker instances, supporting applications with multiple users and stereo AR.
- Advanced 2D-barcode support for high-speed tracking in applications with a large number of markers and / or reduced requirement for human-readable markers.
- Multi-platform support, including Windows, Mac OS X, Linux, iOS and Android, in 32- and 64-bit variants.
- High-speed, low CPU-usage tracking scales well across different CPU speeds and capabilities.
- Line-of-sight inference from head-mounted cameras.