# busy-ring

An all CSS animated busy indicator

![image](https://github.com/feedstation/busy-ring/assets/72626303/3c0849d8-22be-4290-9ed1-13c0c2b8c546)

Demo code (in `index.html`) is set up to use with HTMX hx-indicator<br>
This code includes a fakey JS trigger to test without HTMX

1. Import the CSS

   ```
   @import url('busy-ring.css') screen;
   @import url('htmx-indicator.css') screen; /* only needed for use with HTMX */
   ```

2. Insert an HTML `div` or `span` with `class="busy-ring"` and with four child `div` tags

   - For Vanilla HTML

      ```
      <span class="busy-ring">
          <div></div>
          <div></div>
          <div></div>
          <div></div>
      </span>
      ```

      **Result**: A busy ring that spins forever (until you do the next step)

   - For HTMX

      a. Set the form `hx-indicator` attribute to point at the id of the 'busy-ring' element

      b. Set the `htmx-indicator` class on the 'busy-ring' element itself

      c. Set the role and aria information because you are a good person

      ```
      <body>
          <form hx-indicator="#spinner">
              <!-- form inputs go here -->
              <button id="input-submit" type="submit">
                  <span class="busy-ring htmx-indicator" id="spinner" role="status" aria-hidden="true"><div></div><div></div><div></div><div></div></span>
                  Submit
              </button>
          </form>
      </body>
      ```

3. Use scripting to show and hide the indicator appropriately
  
   HTMX does this by adding and removing the 'htmx-request' class for you:

   ```
   <span class="busy-ring htmx-indicator htmx-request" ...
   ```
