<template>
  <div>
          <ContactText/>
          <Contact/>

  </div>
</template>
<script>
export default {
  name: "About",
  data() {
    return {};
  },
  methods: {},
  components: {
    ContactText: () => import("@/components/ContactText"),
    Contact: () => import("@/components/Contact"),
  }
};
</script>
