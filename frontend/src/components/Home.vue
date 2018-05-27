<template lang="html">
  <section class="home section">
    <h1 class="title is-1">World Cup Sweep</h1>
    <groups></groups>
    <sign-up></sign-up>
  </section>
</template>

<script>
import SignUp from '@/components/SignUp';
import Groups from '@/components/Groups';

export default {
  name: 'home',
  components: { SignUp, Groups },
};
</script>
