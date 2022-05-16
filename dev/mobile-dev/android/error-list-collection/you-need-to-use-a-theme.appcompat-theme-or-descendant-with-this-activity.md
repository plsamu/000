# You need to use a Theme.AppCompat theme (or descendant) with this activity

{% embed url="https://stackoverflow.com/questions/39604889/how-to-fix-you-need-to-use-a-theme-appcompat-theme-or-descendant-with-this-a" %}

> Used to face the same problem. The reason was in incorrect context passing to `AlertDialog.Builder(here)`. Use like AlertDialog.Builder(Homeactivity.this)
