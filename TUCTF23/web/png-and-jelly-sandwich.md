# PNG and Jelly Sandwich

This challenge consists of a webpage that accepts an image and stretches it, supposedly so the author's grandma can see it (I'd love to know what condition she suffers from).

From the description:
> It wasn't that hard at all, I even did it all with open-source software!

and the fact that the output filenames are in the format `IM-{unix seconds}.{unix milliseconds}.png`, we can infer that the server is using ImageMagick to stretch the image.

It uses a version of ImageMagick vulnerable to [CVE-2022-44268](https://github.com/duc-nt/CVE-2022-44268-ImageMagick-Arbitrary-File-Read-PoC), which we can use to get the contents of `flag.txt` in the stretched image. There are several ways to do this, but I used [TweakPNG](https://entropymine.com/jason/tweakpng/) to read it as hex and decoded it in Python.

This gives us the following:
```
Sorry, Grandma viewed this Sunday, November 12, 2023 at exactly 13:23:48 (GMT).
```

From the convention of the output file names, it follows that the file Grandma viewed is likely `IM-1699795428.000000.png` (the 'exactly' in the text is very important, this was clarified with the challenge organizers). This is not accessible by simply requesting `/uploads/IM-1699795428.000000.png`, it has to be obtained through the same vulnerability as the text. This gives us a PNG image containing the flag.