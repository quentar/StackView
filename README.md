Purpose
--------------

StackView is a class designed to simplify the implementation of vertical stacks of views on iOS. You can think of it as a bit like a simplified version of UITableView.

To use StackView, simply add subviews to it, and it will automatically resize and stack them, optionally applying a spacing value between them. This can be done either in code or Interface Builder.

StackView automatically handles view resizing (e.g. in the case of a screen rotation).

Minor modification done to allow collapsing hidden views.


Supported OS & SDK Versions
-----------------------------

* Supported build target - iOS 8.0 (Xcode 6.0, Apple LLVM compiler 6.0)
* Earliest supported deployment target - iOS 5.0
* Earliest compatible deployment target - iOS 4.3

NOTE: 'Supported' means that the library has been tested with this version. 'Compatible' means that the library should work on this OS version (i.e. it doesn't rely on any unavailable SDK features) but is no longer being tested for compatibility and may require tweaking or bug fixes to run correctly.


ARC Compatibility
------------------

StackView works either with or without ARC automatically.


Thread Safety
--------------

StackView is derived from UIView and - as with all UIKit components - it should only be accessed from the main thread.


Installation
--------------

To use the StackView class in an app, just drag the StackView class files (demo files and assets are not needed) into your project.


Properties
--------------

StackView has the following properties:

	@property (nonatomic, assign) CGFloat contentSpacing;
	
This is the spacing (in points) to apply between views in the StackView. You can set this either with code or by using the User Defined Runtime Attributes in Interface Builder.
	
    @property (nonatomic, assign) CGFloat maxHeight;

The maximum height (in points) that the StackView will grow to when you call -sizeToFit. If the content exceeds this height then the StackView will scroll. Note that StackView is a subclass of UIScrollView, so it inherits all of the UIScrollView methods and properties.


Tips
---------------

1.  StackView inherits various useful properties from UIScrollView, including `contentInset`, which lets you inset the StackView subviews from the edge.

2.  StackView will automatically call sizeToFit on all of its subviews. This means that labels, buttons, etc will typically be stretched to the full width of the StackView, and images will be set to their natural size.

    If you don't want this to happen, simply embed your views inside another UIView and StackView will only resize the outer view (see how this is handled with the UIButton in the example project).
    
3.  If you require variable spacing between your StackView items, you can insert a blank view of height 0 to double the `contentSpacing` between two consecutive views, or of height `N` to create a gap of `contentSpacing * 2 + N`.

4.  You can nest StackViews, which is useful if you want to create hierarchical structures, or have groups of views with different `contentSpacing` values.`

5.  If you use a UIScrollView and set its class to StackView in Interface Builder (instead of starting with a plain UIView) then Interface Builder will let you configure properties such as contentInset and scrollbar appearance.


Release notes
----------------

Version 1.0.5

- Fixed extra bottom padding on iPhone 6 plus

Version 1.0.4

- Removed erronious bottom padding
- Now updates layout when sizeToFit is called
- Now compliant with -Weverything warning level

Version 1.0.3

- Layout code is now DRY
- Fixed some edge cases with nested StackViews
- Improved documentation & example project

Version 1.0.2

- Added code to force layout when StackView is resized

Version 1.0.1

- Removed some redundant layout methods
- Improved the example project

Version 1.0

- First release