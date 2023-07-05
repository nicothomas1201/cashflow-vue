<template>
  <Layout>
    <template #header>
      <Header />
    </template>
    <template #resume>
      <Resume
        :label="label"
        :total-amount="100000"
        :amount="amount"
      >
        <template #graphic>
          <Graphic :amounts="amounts" />
        </template>
        <template #action>
          <Action />
        </template>
      </Resume>
    </template>
    <template #movements>
      <Movements
        :movements="movements" 
      />
    </template>
  </Layout>
</template>

<script>
  import Layout from './Layout.vue';
  import Header from './Header.vue';
  import Action from './Action.vue';
  import Resume from './Resume/Index.vue';
  import Movements from './Movements/Index.vue';
  import Graphic from './Resume/Graphic.vue';

  export default {
    components: {
      Layout,
      Header,
      Resume,
      Movements,
      Action,
      Graphic
    },
    data(){
      return {
        label: null,
        amount: null,
        amounts: [100, 200, 500, 200, -400, -600, -300, 0, 300, 500],
        movements: [
          {
            id: 1,
            title: "Movimiento",
            description: "Deposito de salario",
            amount: "1000",
          },
          {
            id: 2,
            title: "Movimiento 1",
            description: "Deposito de honorarios",
            amount: "500",
          },
          {
            id: 3,
            title: "Movimiento 3",
            description: "Comida",
            amount: "-100",
          },
          {
            id: 4,
            title: "Movimiento 4",
            description: "Colegiatura",
            amount: "1000",
          },
          {
            id: 5,
            title: "Movimiento 5",
            description: "Reparación equipo",
            amount: "1000",
          },
        ]
      }
    }
  }
</script>