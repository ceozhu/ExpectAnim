# ExpectAnim

Describe your animation and run !

[![gif](https://raw.githubusercontent.com/florent37/ExpectAnim/master/media/sample.gif)](https://github.com/florent37/ExpectAnim)

```java
new ExpectAnim()

                .expect(avatar)
                .toBe(
                    Expectations...
                )
                .start();
```

#Download

<a href='https://ko-fi.com/A160LCC' target='_blank'><img height='36' style='border:0px;height:36px;' src='https://az743702.vo.msecnd.net/cdn/kofi1.png?v=0' border='0' alt='Buy Me a Coffee at ko-fi.com' /></a>

In your module [![Download](https://api.bintray.com/packages/florent37/maven/ExpectAnim/images/download.svg)](https://bintray.com/florent37/maven/ExpectAnim/_latestVersion)
```groovy
compile 'com.github.florent37:expectanim:1.0.0'
```

This code describe the video above

```java
new ExpectAnim()

                .expect(avatar)
                .toBe(
                        bottomOfParent().withMarginDp(16),
                        leftOfParent().withMarginDp(16),
                        width(40).toDp().keepRatio()
                )

                .expect(name)
                .toBe(
                        toRightOf(avatar).withMarginDp(16),
                        sameCenterVerticalAs(avatar),
                        toHaveTextColor(Color.WHITE)
                )

                .expect(subname)
                .toBe(
                        toRightOf(name).withMarginDp(5),
                        sameCenterVerticalAs(name),
                        toHaveTextColor(Color.WHITE)
                )

                .expect(follow)
                .toBe(
                        rightOfParent().withMarginDp(4),
                        bottomOfParent().withMarginDp(12),
                        toHaveBackgroundAlpha(0f)
                )

                .expect(message)
                .toBe(
                        aboveOf(follow).withMarginDp(4),
                        rightOfParent().withMarginDp(4),
                        toHaveBackgroundAlpha(0f)
                )

                .expect(bottomLayout)
                .toBe(
                        atHisOriginalPosition()
                )

                .expect(content)
                .toBe(
                        atHisOriginalPosition(),
                        visible()
                )

                .toAnimation()
                .setDuration(1500)

                .start();
```

## Follow scroll

[![gif](https://raw.githubusercontent.com/florent37/ExpectAnim/master/media/scroll.gif)](https://github.com/florent37/ExpectAnim)

Use `setPercent` to apply modify the current step of the animation

Exemple with a scrollview

```java
this.expectAnimMove = new ExpectAnim()
                .expect(username)
                .toBe(
                        toRightOf(avatar).withMarginDp(16),
                        sameCenterVerticalAs(avatar),
                        alpha(0.5f)
                )

                .expect(avatar)
                .toBe(
                        topOfParent(),
                        leftOfParent().withMarginDp(16),
                        scale(0.5f, 0.5f)
                )
                .expect(follow)
                .toBe(
                        rightOfParent().withMarginDp(16),
                        sameCenterVerticalAs(avatar)
                )

                .expect(backbground)
                .toBe(
                        height(height).withGravity(Gravity.LEFT, Gravity.TOP)
                )

                .toAnimation();

scrollView.setOnScrollChangeListener(new NestedScrollView.OnScrollChangeListener() {
    @Override
    public void onScrollChange(NestedScrollView v, int scrollX, int scrollY, int oldScrollX, int oldScrollY) {
        final float percent = (scrollY * 1f) / v.getMaxScrollAmount();

        expectAnimMove.setPercent(percent);
    }
});
```

## Apply directly

Use `setNow` to apply directly the transformation

```java
new ExpectAnim()
                .expect(view)
                .toBe(
                        outOfScreen(Gravity.BOTTOM)
                )
                .toAnimation()
                .setNow();
```

# List of expectations

```
new ExpectAnim()
                .expect(view)
                .toBe(

                    //.withMargin(marginPx)
                    //.withMarginDp(margin)
                    //.withMarginDimen(R.dimen.margin)

                    toRightOf(view)
                    toLeftOf(view)
                    belowOf(view)
                    aboveOf(view)

                    atHisOriginalPosition()


                    sameCenterAs(view, horizontal, vertical)
                    sameCenterHorizontalAs(view)
                    sameCenterVerticalAs(view)
                    centerInParent(horizontal, vertical)
                    centerVerticalInParent()
                    centerHorizontalInParent()

                    centerBetweenViews(view1, view2, horizontal, vertical)
                    centerBetweenViewAndParent(otherView, horizontal, vertical, toBeOnRight, toBeOnBottom)

                    topOfParent()
                    rightOfParent()
                    bottomOfParent()
                    leftOfParent()

                    alignBottom(otherView)
                    alignTop(otherView)
                    alignLeft(otherView)
                    alignRight(otherView)

                    outOfScreen(gravitiy)  //Gravity.LEFT / Gravity.RIGHT / Gravity.TOP / Gravity.BOTTOM

                    alpha(alpha)
                    sameAlphaAs(otherView)
                    visible()
                    invisible()

                    //.keepRatio()
                    //.withGravity(horizontalGravity, verticalGravity)

                    atHisOriginalScale()

                    scale(scaleX, scaleY)
                    height(height)
                    width(width)
                    sameScaleAs(otherView)
                    sameWidthAs(otherView)
                    sameHeightAs(otherView)


                    toHaveTextColor(textColor)
                    toHaveBackgroundAlpha(alpha)

                )

```

#Credits

Author: Florent Champigny

<a href="https://plus.google.com/+florentchampigny">
  <img alt="Follow me on Google+"
       src="https://raw.githubusercontent.com/florent37/DaVinci/master/mobile/src/main/res/drawable-hdpi/gplus.png" />
</a>
<a href="https://twitter.com/florent_champ">
  <img alt="Follow me on Twitter"
       src="https://raw.githubusercontent.com/florent37/DaVinci/master/mobile/src/main/res/drawable-hdpi/twitter.png" />
</a>
<a href="https://fr.linkedin.com/in/florentchampigny">
  <img alt="Follow me on LinkedIn"
       src="https://raw.githubusercontent.com/florent37/DaVinci/master/mobile/src/main/res/drawable-hdpi/linkedin.png" />
</a>

#License

    Copyright 2017 florent37, Inc.

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
