+++
date = "2016-12-30T16:01:21-08:00"
title = "Intro Screens"
list_item_layout = "list-item-media-left"

media_src = "intro-screens"
media_title = "Intro Screens"
media_type = "video"
+++

The [Logos Bible](https://play.google.com/store/apps/details?id=com.logos.androidlogos) introduction screens give users a preliminary glimpse of core features in the app prior to signing in. A cubic easing algorithm in combination with a linear offset that is staggered from top to bottom creates an appealing visual effect.

In development I encountered an issue where the VideoView would not render its paused video while horizontal scrolling. Essentially, VideoView's base class SurfaceView does not [update its window](https://android.googlesource.com/platform/frameworks/base/+/nougat-mr1-release/core/java/android/view/SurfaceView.java#686) when ViewPager.PageTransformer sets its layer to View.LAYER_TYPE_HARDWARE during transformation.

One option was to disable hardware acceleration during page transformation. But this caused visible lagging, leaving un-rendered black boxes to the left or right of the video during horizontal scrolling. The final solution was to support hardware acceleration by implementing a VideoView that extended TextureView instead of SurfaceView.<!--more-->

Another challenge was scaling the both the video and the phone outline correctly. Since a VideoView scales itself and its video separately, it can be tricky to support varying screen sizes when the video itself (as opposed to the parent VideoView) must match the scale of another View.

The solution was to wrap the VideoView with a custom ViewGroup that scaled according to a fixed aspect ratio. This forced the VideoView to maintain the same aspect ratio as the video while leaving its sizing behavior in tact.
