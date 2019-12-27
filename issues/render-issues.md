<main>

  <div class="wrapper">
  
  # Flexbox bugs 1
  
  This currently only effects Chrome, Opera, and Edge because these browsers render certain elements differently making them inelligble for certain flex styles.
  
  ## Fieldsets
  
  Although the `<fieldset>` wrapping the elements is set to `display: flex;` the elements don't respect that. They should be on the same row and wrap to the next if there's not enough space, but instead they stack. Open this pen in Firefox and see the below example matches the next (see solution).
  
<form>
  
<fieldset class="d-flex"><legend class="col-1-4">Monster Preference:</legend>
  
  <div class="col-1-4"><input type="radio" id="kraken-1" name="monster"> <label for="kraken-1">Kraken</label></div>
  
  <div class="col-1-4"><input type="radio" id="sasquatch-1" name="monster"> <label for="sasquatch-1">Sasquatch</label></div>
  
  <div class="col-1-4"><input type="radio" id="mothman-1" name="monster"> <label for="mothman-1">Mothman</label></div>
  
</fieldset>
  
</form>
  
  ### The solution
  
  Wrap the inner elements with a `<div>` and add `display: flex;` to that. Note, do not wrap the `<legend>` element in the `<div>` otherwise your code will flag validators.
  
  <form>
  
  <fieldset class="checkbox-cards"><legend class="col-1-4">Monster Preference:</legend>
  
  <div class="d-flex">
  
  <div class="col-1-4"><input type="radio" id="kraken-2" name="monster"> <label for="kraken-2">Kraken</label></div>
  
  <div class="col-1-4"><input type="radio" id="sasquatch-2" name="monster"> <label for="sasquatch-2">Sasquatch</label></div>
  
  <div class="col-1-4"><input type="radio" id="mothman-2" name="monster"> <label for="mothman-2">Mothman</label></div>
  
  </div>
  
  </fieldset>
  
  </form>
  
  ### What if you need a legend to flex?
  
  For similar reasoning that `<fieldset>` cannot be a flex container the `<legend>` element cannot be a flex item. The only cross-browser solution I've managed to come up with is positioning it absolute and offsetting the first flex item to accomodate for it.
  
  <form>
  
  <fieldset class="p-relative"><legend class="legend-illusion p-absolute">Monster Preference:</legend>
  
  <div class="d-flex">
  
  <div class="col-1-4 offset-legend"><input type="radio" id="kraken-3" name="monster"> <label for="kraken-3">Kraken</label>  
  </div>
  
  <div class="col-1-4"><input type="radio" id="sasquatch-3" name="monster"> <label for="sasquatch-3">Sasquatch</label>  
  </div>
  
  <div class="col-1-4"><input type="radio" id="mothman-3" name="monster"> <label for="mothman-3">Mothman</label></div>
  
  </div>
  
  </fieldset>
  
  </form>
  
  </div>
  
  </main>