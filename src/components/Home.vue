<template>
  <Layout>
    <template #header>
      <Header />
    </template>
    <template #resume>
      <Resume
        :label="'Junio 2023'"
        :total-amount="100000"
        :amount="10000"
      />
    </template>
    <template #movements>
      <Movements />
    </template>
  </Layout>
</template>

<script>
  import Layout from './Layout.vue';
  import Header from './Header.vue';
  import Resume from './Resume/Index.vue';
  import Movements from './Movements.vue';

  export default {
    components: {
      Layout,
      Header,
      Resume,
      Movements,
    }
  }
</script>