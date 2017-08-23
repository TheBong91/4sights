# High Tech Pioneer


### Ingredients

This site uses
* css Template HTML5Up @assets/css/main.css https://html5up.net/
* font-awesome icons @assets/fonts/ http://fontawesome.io/
* fullpage.js delivering the js to scroll through pages https://alvarotrigo.com/fullPage/
* Benchmarkmail Signup Form and Contacts Manager (check email to Thorsten/Lucas) https://www.benchmarkemail.com/


### Customization

The @assets/js/main.js file contains the customization

* Background and Delay Time of Background pictures (line 34 ff.)
```javascript
// Slideshow Background.
  (function() {

    // Settings.
      var settings = {

        // Images (in the format of 'url': 'alignment').
          images: {
            'images/zzz.jpg': 'center ',
            'images/xx.jpg': 'center ',
            'images/yyy.jpg': 'center ',
            'images/ttt.jpg': 'right bottom',
          },

        // Delay.
          delay: 5000

      };
  ```

  * Frontend Javascript EventHook for FormSubmit
  ```javascript
  // Events.
  // Note: If you're *not* using AJAX, get rid of this event listener.
    $form.addEventListener('submit', function(event) {
      // var $code = document.querySelectorAll("#signup-form #email").value;
      // console.log($code);

      var $code2 = event.target[0].value || event.srcElement[0].value;

      event.stopPropagation();
      event.preventDefault();

      // Hide message.
        $message._hide();

      // Disable submit.
        $submit.disabled = true;

      // Process form.
      // Note: Doesn't actually do anything yet (other than report back with a "thank you"),
      // but there's enough here to piece together a working AJAX submission call that does.
        window.setTimeout(function() {

          $message.classList.remove('failure');
          // Reset form.
            $form.reset();

          // Enable submit.
            $submit.disabled = false;

            if($list.includes($code2)){
              // Show message.
                $message._show('success', 'Code is correct!');

                window.setTimeout(function() {
                  window.location.replace('#successCode');
                }, 750);
            } else {
              $message._show('failure', 'Wrong code!');
            }

        }, 750);

```

* Code Validation (line 11 ff)
```javascript
// Vars.
  var $form = document.querySelectorAll('#signup-form')[0],
    $submit = document.querySelectorAll('#signup-form input[type="submit"]')[0],
    // Validation Codes
    $list = ["abc", "bcd", "asd", "code", "test"],
    $message;

```

* Javscript for Benchmarkmail at index.html (lines 96 ff) is copied from https://www.benchmarkemail.com/

* Initialisation of fullPager slide and config at index.html (lines 85 ff)
```javascript
<script type="text/javascript">
  fullpage.initialize('#fullpage', {
    anchors: ['enterCode', 'successCode'],
    menu: '#menu',
    css3:true,
    keyboardScrolling:false,
    animateAnchor: false
  });
</script>
```
