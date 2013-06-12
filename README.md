#Arpan Jpeg Encoder

A github repository for code originally posted to CodeProject:

http://www.codeproject.com/Articles/83225/A-Simple-JPEG-Encoder-in-C

Which itself is a translation of a C project "from a forum" - where is not stated.

The version here simplifies the main encoder call a bit so you can skip implementing the 2 interfaces for handling progress updates (for example if you're running this on a server, or just want to keep the call simple).

It also upgrades the code to .Net 4.5.

If you just want to save a System.Drawing.Image, reference JpegEncoderCore.csproj use this sample code:

	var jpegEnc = new JpegEncoder.BaseJPEGEncoder();
	jpegEnc.Save(image, @"C:\test.jpg", 50);

The image here is your System.Drawing.Image. The path can be whatever you like. The final value is the Quantization value, which at 1 is basically lossless and can result in very large files, and at high values like 1000 can be a bit smaller and really look terrible.

The encoder is worse in terms of quality for size than common encoders out there like Gimp or Photoshop, but can produce much higher quality files than the built-in .Net encoder. A quantizer value of 100 gets pretty good quality perhaps comparable to Photoshop's 30% (much higher file size however), and a value of 10 gets near-lossless quality with file sizes larger than Photoshop is capable of producing at 100%.


##License
The code is licensed under the Code Project License:
http://www.codeproject.com/info/cpol10.aspx

Although the original C code may have been under a different license - unknown.