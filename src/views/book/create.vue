<template>
  <div>
    <detail ref="details" :is-edit="isEdit"></detail>
  </div>
</template>

<script>
/* eslint-disable */
import Detail from "./components/detail";
export default {
  components: { Detail },
  data() {
    return {
      isEdit: false,
    };
  },
  created() {},
  mounted() {},
  methods: {
    func() {},
  },
};

</script>
