# Vue Cookie Banner Test

The test only gave App.vue and CookieBanner.vue initially.

## Requirement of done (that i remembered)

1. To be able to click Accept or Decline button
2. To be able to use key press A or D to achieve No.1
3. Store user preference into localstorage
4. If user does not accept, do not show them the content and create an alert
5. Use value from localstorage to determine whether to show content or not whenever user refresh the page.
6. App.vue should never access localstorage directly.
7. CookieBanner.vue should be resposible for clearing out any event listeners
