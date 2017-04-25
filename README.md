showUpButton function:
```java
private void showUpButton(boolean show) {

    if(show) {
        toggle.setDrawerIndicatorEnabled(false);
        ObjectAnimator.ofFloat(toggle.getDrawerArrowDrawable(), "progress", 1).start();
        actionBar.setDisplayHomeAsUpEnabled(true);
        if(!mToolBarNavigationListenerIsRegistered) {
            toggle.setToolbarNavigationClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View v) {
                    onBackPressed();
                }
            });
            mToolBarNavigationListenerIsRegistered = true;
        }

    } else {
        actionBar.setDisplayHomeAsUpEnabled(false);
        ObjectAnimator.ofFloat(toggle.getDrawerArrowDrawable(), "progress", 0).start();
        toggle.setDrawerIndicatorEnabled(true);
        toggle.setToolbarNavigationClickListener(null);
        mToolBarNavigationListenerIsRegistered = false;
    }
}
```

Animated object listener:
```java
animation.addListener(new Animator.AnimatorListener() {
                @Override
                public void onAnimationStart(Animator animation) {

                }

                @Override
                public void onAnimationEnd(Animator animation) {
                    Toast.makeText(VideoEditorActivity.this, "animation ended", Toast.LENGTH_LONG).show();
                }

                @Override
                public void onAnimationCancel(Animator animation) {

                }

                @Override
                public void onAnimationRepeat(Animator animation) {

                }
            });
```
