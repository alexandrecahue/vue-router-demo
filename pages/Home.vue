<template>
  <div class="page">
    This is the homepage.<br />It has default header and footer.
  </div>
</template>

<script>
export default {
  name: "home-page",
  beforeRouteLeave(to, from, next) {
    let message = "Are you sure?";

    let options = {
      html: false, // set to true if your message contains HTML tags. eg: "Delete <b>Foo</b> ?"
      loader: false, // set to true if you want the dailog to show a loader after click on "proceed"
      reverse: false, // switch the button positions (left to right, and vise versa)
      okText: "Continue",
      cancelText: "Close",
      animation: "zoom", // Available: "zoom", "bounce", "fade"
      type: "basic", // coming soon: 'soft', 'hard'
      verification: "continue", // for hard confirm, user will be prompted to type this to enable the proceed button
      verificationHelp: 'Type "[+:verification]" below to confirm', // Verification help text. [+:verification] will be matched with 'options.verification' (i.e 'Type "continue" below to confirm')
      clicksCount: 3, // for soft confirm, user will be asked to click on "proceed" btn 3 times before actually proceeding
      backdropClose: false, // set to true to close the dialog when clicking outside of the dialog window, i.e. click landing on the mask
      customClass: "", // Custom class to be injected into the parent node for the current dialog instance
    };
    this.$dialog
      .confirm(message, options)
      .then(function () {
        next();
      })
      .catch(function () {
        next(false);
      });
  },
};
</script>
