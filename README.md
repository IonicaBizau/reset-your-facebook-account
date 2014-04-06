Reset Your Facebook Account
===========================

Sometimes you want to start your Facebook activity again. So, here are some useful scripts to delete your Facebook posts, comments and likes.

## Prerequisites

Define the following function (that includes jQuery on the page) before running the scripts:

```js
function loadScript(url, callback) {

    var script = document.createElement("script")
    script.type = "text/javascript";

    if (script.readyState) { //IE
        script.onreadystatechange = function () {
            if (script.readyState == "loaded" || script.readyState == "complete") {
                script.onreadystatechange = null;
                callback();
            }
        };
    } else { //Others
        script.onload = function () {
            callback();
        };
    }

    script.src = url;
    document.getElementsByTagName("head")[0].appendChild(script);
}
```
([Thanks](http://www.jquery4u.com/javascript/dynamically-load-jquery-library-javascript/)!)

Replace `your-facebook-username` in URLs with your Facebook username. Then start hacking. :smile:

## Likes

> https://www.facebook.com/your-facebook-username/allactivity?privacy_source=activity_log&log_filter=likes

```js
loadScript("//code.jquery.com/jquery-1.11.0.min.js", function () {
  setInterval(function () {
    var last = $("._6a._6b.uiPopover.rfloat a span").last().click();
    $("span:contains(Unlike):visible").click();
    last.closest("table").remove();
  }, 1000);
});
```

## Posts

> https://www.facebook.com/your-facebook-username/allactivity?privacy_source=activity_log&log_filter=cluster_11

```js
loadScript("//code.jquery.com/jquery-1.11.0.min.js", function () {
  setInterval (function () {
    var last = $("._6a._6b.uiPopover.rfloat a span").last().click();
    $("span:contains(Delete):visible").click();
    setTimeout(function () {
      $("button:contains(Delete Post):visible").click();
      last.closest("table").remove();
    }, 1000);
  }, 7000);
});
```

## Comments

> https://www.facebook.com/your-facebook-username/allactivity?privacy_source=activity_log&log_filter=cluster_116

```js
loadScript("//code.jquery.com/jquery-1.11.0.min.js", function () {
  setInterval (function () {
    var last = $("._6a._6b.uiPopover.rfloat a span").last().click();
    $("span:contains(Delete):visible").click();
    last.closest("table").remove();
  }, 2000);
});
```

If you find a bug, have a question or want a feature to be added, open [an issue](https://github.com/IonicaBizau/reset-your-facebook-account/issues).

# License
See LICENSE file.
