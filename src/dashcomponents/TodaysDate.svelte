<script>
  import moment from "moment";
</script>

<style>
  legend {
    text-align: center;
  }
  fieldset {
    border-radius: 15px;
    width: fit-content;
    margin: 2px auto;
  }
</style>

<fieldset>
  <legend>Today's Date:</legend>

  <h3>{moment().format('hh:mm A, Do MMM YYYY')}</h3>
</fieldset>
