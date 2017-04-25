showUpButton function:
```java
private void showUpButton(boolean show) {

        if(show) {
            ObjectAnimator animation =ObjectAnimator.ofFloat(toggle.getDrawerArrowDrawable(), "progress", 1);
            animation.addListener(new Animator.AnimatorListener() {
                @Override
                public void onAnimationEnd(Animator animation) {
                    toggle.setDrawerIndicatorEnabled(false);
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
                }
                @Override
                public void onAnimationStart(Animator animation) {}
                @Override
                public void onAnimationCancel(Animator animation) {}
                @Override
                public void onAnimationRepeat(Animator animation) {}
            });
            animation.start();

        } else {
            actionBar.setDisplayHomeAsUpEnabled(false);
            ObjectAnimator.ofFloat(toggle.getDrawerArrowDrawable(), "progress", 0).start();
            toggle.setDrawerIndicatorEnabled(true);
            toggle.setToolbarNavigationClickListener(null);
            mToolBarNavigationListenerIsRegistered = false;
        }
    }
```
