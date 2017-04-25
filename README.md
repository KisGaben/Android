showUpButton függvény:
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
