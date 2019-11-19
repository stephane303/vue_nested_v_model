<template>
  <div class="input-group date">
    <input type="text" class="form-control" 
        :value="localState" 
        @input="(newLocalState) => {localState = newLocalState}" />
    <span class="input-group-addon">
      <span class="glyphicon glyphicon-calendar"></span>
    </span>
  </div>
</template>

<script>
export default {
  name: "vue-datetimepicker",
  props: ["value"],
  watch: {
    options: function(options) {
      // update options
      $(this.$el).datetimepicker({ data: options });
    }
  },
  mounted: function() {
    var vm = this;
    var mycomp = $(this.$el).datetimepicker({
      format: "DD-MM-YYYYTHH:MM A"
    });
    mycomp.on("dp.change", function(e) {
      vm.localState = e.date;
    });
  },
  destroyed: function() {
    $(this.$el)
      .off()
      .datetimepicker("destroy");
  },
  computed: {
    localState: {
      get() {
        return this.value;
      },
      set(localState) {
        console.log(localState);
        this.$emit("input", localState.format("DD-MM-YYYY HH:MM A"));
      }
    }
  }
};
</script>