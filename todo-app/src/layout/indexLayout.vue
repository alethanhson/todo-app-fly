<template>
  <HeaderLayoutCP />

  <Container>
    <main>
      <slot />
    </main>
    <FooterLayoutCP />
  </Container>
</template>

<script>
import Container from "@/components/ContainerAT.vue";
import HeaderLayoutCP from "./components/HeaderLayout..vue";
import FooterLayoutCP from "./components/FooterLayout.vue";

export default {
  components: {
    Container,
    HeaderLayoutCP,
    FooterLayoutCP,
  },
};
</script>
