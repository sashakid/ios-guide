- [Autolayout](#autolayout)

# Autolayout

_"Use Auto Layout"_ determines whether a storyboard uses the Auto Layout features introduced in iOS 6 to automatically layout your interface using constraints.

_"Use Size Classes"_ enables a new Xcode 6 feature called size classes that lets you use Auto Layout to build one interface for all devices and customize constraint constants, and certain views and constraints for different interface idioms while reusing the general layout. It saves the work and repetitiveness of having to build and maintain both MainiPhone and MainiPad storyboards.

__External Changes__

External changes occur when the size or shape of your superview changes.

__Internal Changes__

Internal changes occur when the size of the views or controls in your user interface change.

There are three main approaches to laying out a user interface.

1. you can programmatically lay out the user interface
2. you can use autoresizing masks to automate some of the responses to external change
3. you can use Auto Layout.

The frame defined the view’s origin, height, and width in the superview’s coordinate system.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/autolayout_frame1.png"><img src="https://github.com/sashakid/ios-guide/blob/master/Images/autolayout_frame2.png">

The layout of your view hierarchy is defined as a series of linear equations. Each constraint represents a single equation. Your goal is to declare a series of equations that has one and only one possible solution.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/autolayout.png">

When calculating solutions, Auto Layout attempts to satisfy all the constraints in priority order from highest to lowest. If it cannot satisfy an optional constraint, that constraint is skipped and it continues on to the next constraint.

Some views have a natural size given their current content. This is referred to as their _intrinsic content size_.

__The content hugging__ pulls the view inward so that it fits snugly around the content.

__The compression resistance__ pushes the view outward so that it does not clip the content.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/intrinsic.png">

```
// Compression Resistance
View.height >= 0.0 * NotAnAttribute + IntrinsicHeight
View.width >= 0.0 * NotAnAttribute + IntrinsicWidth

// Content Hugging
View.height <= 0.0 * NotAnAttribute + IntrinsicHeight
View.width <= 0.0 * NotAnAttribute + IntrinsicWidth
```
These properties only take effect for views which define an intrinsic content size, otherwise there is no content size defined that could resist compression or be hugged.
The top and bottom layout guides represent the upper and lower edge of the visible content area for the currently active view controller.

Auto Layout does not operate on views’ frame, but on their alignment rect. It’s easy to forget the subtle difference, because in many cases they are the same.

Unsatisfiable layouts occur when the system cannot find a valid solution for the current set of constraints. Two or more required constraints conflict, because they cannot all be true at the same time.
When the system detects a unsatisfiable layout at runtime, it performs the following steps:

1. Auto Layout identifies the set of conflicting constraints.
2. It breaks one of the conflicting constraints and checks the layout. The system continues to break constraints until it finds a valid layout.
3. Auto Layout logs information about the conflict and the broken constraints to the console.

As soon as you know about the error, the solution is typically very straightforward. Either remove one of the constraints, or change it to an optional constraint.

Ambiguous layouts occur when the system of constraints has two or more valid solutions. There are two main causes:

1. The layout needs additional constraints to uniquely specify the position and location of every view. After you determine which views are ambiguous, just add constraints to uniquely specify both the view’s position and its size.
2. The layout has conflicting optional constraints with the same priority, and the system does not know which constraint it should break.

Here, you need to tell the system which constraint it should break, by changing the priorities so that they are no longer equal. The system breaks the constraint having the lowest priority first.
When an ambiguous layout occurs at runtime, Auto Layout chooses one of the possible solutions to use. This means the layout may or may not appear as you expect. Furthermore, there are no warnings written to the console, and there is no way to set a breakpoint for ambiguous layouts.
There are a few methods you can call to help identify ambiguous layouts. All of these methods should be used only for debugging. Set a breakpoint somewhere where you can access the view hierarchy, and then call one of the following methods from the console:

`hasAmbiguousLayout` Available for both iOS and OS X. Call this method on a misplaced view. It returns YES if the view’s frame is ambiguous. Otherwise, it returns NO.

`exerciseAmbiguityInLayout` Available for both iOS and OS X. Call this method on a view with ambiguous layout. This will toggle the system between the possible valid solutions.

`constraintsAffectingLayoutForAxis:` Available for iOS. Call this method on a view. It returns an array of all the constraints affecting that view along the specified axis.

`constraintsAffectingLayoutForOrientation` Available for OS X. Call this method on a view. It returns an array of all the con-straints affecting that view along the specified orientation.

`_autolayoutTrace` Available as a private method in iOS. Call this method on a view. It returns a string with diagnostic information about the entire view hierarchy containing that view. Ambiguous views are labeled, and so are views that have translatesAutoresizingMaskIntoConstraints set to YES.

Four of these are the Final size classes:

1. Compact-Compact
2. Compact-Regular
3. Regular-Compact
4. Regular-Regular

Base size classes:

5. Compact-Any
6. Regular-Any
7. Any-Compact
8. Any-Regular
9. Any-Any

It is typically easiest to work from the most general size class to the most specific. Select the default layout for your app, and design this layout in the Any-Any size class. Then modify the other Base or Final size classes as needed.

Compared to working with springs and struts, Auto Layout introduces two additional steps to the process before views can be displayed:

* updating constraints
* laying out views

Each step is dependent on the one before; display depends on layout, and layout depends on updating constraints.

The first step – updating constraints – can be considered a “measurement pass.” It happens bottom-up (from subview to super view) and prepares the information needed for the layout pass to actually set the views’ frame. You can trigger this pass by calling setNeedsUpdateConstraints. Any changes you make to the system of constraints itself will automatically trigger this. However, it is useful to notify Auto Layout about changes in custom views that could affect the layout. Speaking of custom views, you can override `updateConstraints` to add the local constraints needed for your view in this phase.

The second step – layout – happens top-down (from super view to subview). This layout pass actually applies the solution of the constraint system to the views by setting their frames (on OS X) or their center and bounds (on iOS). You can trigger this pass by calling `setNeedsLayout`, which does not actually go ahead and apply the layout immediately, but takes note of your request for later. This way you don’t have to worry about calling it too often, since all the layout requests will be coalesced into one layout pass.
To force the system to update the layout of a view tree immediately, you can call `layoutIfNeeded` / `layoutSubtreeIfNeeded` (on iOS and OS X respectively). This can be helpful if your next steps rely on the views’ frame being up to date. In your custom views you can override `layoutSubviews` / `layout` to gain full control over the layout pass.

Finally, the display pass renders the views to screen and is independent of whether you’re using Autolayout or not. It operates top-down and can be triggered by calling `setNeedsDisplay`, which results in a deferred redraw coalescing all those calls. Overriding the familiar `drawRect:` is how you gain full control over this stage of the display process in your custom views.

Since each step depends on the one before it, the display pass will trigger a layout pass if any layout changes are pending. Similarly, the layout pass will trigger updating the constraints if the constraint system has pending changes.

It’s important to remember that these three steps are not a one-way street. Constraint-based layout is an iterative process. The layout pass can make changes to the constraints based on the previous layout solution, which again triggers updating the constraints following another layout pass. This can be leveraged to create advanced layouts of custom views, but you can also get stuck in an infinite loop if every call of your custom implementation of layoutSubviews results in another layout pass.
