# UIFont-TTF
UIFont category that allows loading local TrueType font files. This does NOT require defining fonts in the Info.plist file of the project. It is also specifically useful for Cydia Substrate extensions, where modifying the Info.plist is not viable.

##Example Usage

###From a Path:
``` objective-c
    NSString *pathToFont = [[NSBundle mainBundle] pathForResource:@"segoeui" ofType:@"ttf"];
    UIFont *smallFontFromPath = [UIFont fontWithTTFAtPath:pathToFont size:18.0f];
```

###From a Local File URL:
``` objective-c
    NSString *pathToFont = [[NSBundle mainBundle] pathForResource:@"segoeui" ofType:@"ttf"];
    
    NSURL *URLToFont = [NSURL fileURLWithPath:pathToFont];
    UIFont *smallFontFromURL = [UIFont fontWithTTFAtURL:[NSURL fileURLWithPath:pathToFont] size:18.0f];
```

###Notes:
- This category requires ARC, as Non-ARC code is compatible with casting to many Core* types directly, whereas ARC requires __bridge casts.
- Errors are generated by means of NSAssert. If NS_BLOCK_ASSERTIONS has been defined errors will not throw exceptions but instead fail silently. In this even, the font returned will be obtained from systemFontOfSize, taking into account the provided font

##Contact:

Website [http://nin9tyfour.com/](http://nin9tyfour.com/)

Follow [@nin9tyfour on Twitter](http://twitter.com/nin9tyfour)