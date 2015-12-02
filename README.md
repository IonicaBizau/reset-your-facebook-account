# reset-your-facebook-account [![Support this project][donate-now]][paypal-donations]

Sometimes you want to start your Facebook activity again. So, here are some useful scripts to delete your Facebook posts, comments and likes.

## Prerequisites

Install [this Chrome extension](https://chrome.google.com/webstore/detail/jquery-injector/indebdooekgjhkncmgbkeopjebofdoid?hl=en) to include jQuery on the page.

Replace `your-facebook-username` in URLs with your Facebook username. Then start hacking. :smile:

## Likes
> https://www.facebook.com/your-facebook-username/allactivity?privacy_source=activity_log&log_filter=likes

```js
$("html, body").animate({ scrollTop: $(document).height() }, "slow");
setInterval(function () {
  var last = $("._6a._6b.uiPopover.rfloat a span").last().click();
  $("span:contains(Unlike):visible").click();
  var post = last.closest(".pam");
  post.prev().remove();
  post.remove();
}, 700);
```
## Posts
> https://www.facebook.com/your-facebook-username/allactivity?privacy_source=activity_log&log_filter=cluster_11

```js
$("html, body").animate({ scrollTop: $(document).height() }, "slow");
setInterval (function () {
  var last = $("._6a._6b.uiPopover.rfloat a span").last().click();
  $("span:contains(Delete):visible").click();
  setTimeout(function () {
    $("button:contains(Delete Post):visible").click();
    last.closest("table").remove();
  }, 1000);
}, 7000);
```
## Comments
> https://www.facebook.com/your-facebook-username/allactivity?privacy_source=activity_log&log_filter=cluster_116

```js
$("html, body").animate({ scrollTop: $(document).height() }, "slow");
setInterval (function () {
  var last = $("._6a._6b.uiPopover.rfloat a span").last().click();
  $("span:contains(Delete):visible").click();
  var post = last.closest("[data-ft]");
  post.prev().remove();
  post.remove();
}, 400);
```

If you find a bug, have a question or want a feature to be added, open [an issue](https://github.com/IonicaBizau/reset-your-facebook-account/issues).

## Delete messages
```js
var i = setInterval(function () {
  $ul = $("#wmMasterViewThreadlist")
  if (!$ul.find("li").length) return clearInterval(i);
  $ul.find("li").last().find("span").click()
  $("button:contains('Actions')").click()
  $("span:contains('Delete Conversation...')").click()
  $("input[value='Delete Conversation']").click()
}, 500);
```

## How to contribute
Have an idea? Found a bug? See [how to contribute][contributing].

## License

[MIT][license] © [Ionică Bizău][website]

[paypal-donations]: https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=RVXDDLKKLQRJW
[donate-now]: http://i.imgur.com/6cMbHOC.png

[license]: http://showalicense.com/?fullname=Ionic%C4%83%20Biz%C4%83u%20%3Cbizauionica%40gmail.com%3E%20(http%3A%2F%2Fionicabizau.net)&year=2014#license-mit
[website]: http://ionicabizau.net
[contributing]: /CONTRIBUTING.md
[docs]: /DOCUMENTATION.md