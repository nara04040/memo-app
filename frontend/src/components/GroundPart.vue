<template>
  <div class="ground">
    <HeaderPart></HeaderPart>
    <MemoPart></MemoPart>
    <FooterPart></FooterPart>
  </div>
</template>

<script>
import HeaderPart from "./HeaderPart.vue";
import MemoPart from "./MemoPart.vue";
import FooterPart from "./FooterPart.vue";
export default { components: { HeaderPart, MemoPart, FooterPart } };
</script>
