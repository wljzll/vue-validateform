<template>
   <form>
     <slot></slot>
   </form>
</template>
<script>
export default {
  provide() {
    return {
      form: this,
    };
  },
  props: {
   rules: {
     type: Object
   }
  },
  methods: {
    validate(cb) {
      // 执行所有的FormItem的方法
      const tasks = this.$children
        .filter((v) => v.prop)
        .map((item) => item.validate());

      Promise.all(tasks)
        .then(() => cb(true))
        .catch(() => cb(false));
    },
  },
};
</script>
