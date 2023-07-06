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
        // amounts: [100, 200, 500, 200, -400, -600, -300, 0, 300, 500],
        movements: [
          {
            id: 1,
            title: "Movimiento 1",
            description: "Deposito de salario",
            amount: 100,
            time: new Date("07-02-2023"),
          },
          {
            id: 2,
            title: "Movimiento 2",
            description: "Deposito de honorarios",
            amount: 200,
            time: new Date("07-02-2023"),
          },
          {
            id: 3,
            title: "Movimiento 3",
            description: "Comida",
            amount: 500,
            time: new Date("07-02-2023"),
          },
          {
            id: 4,
            title: "Movimiento 4",
            description: "Colegiatura",
            amount: 200,
            time: new Date("07-02-2023"),
          },
          {
            id: 5,
            title: "Movimiento 5",
            description: "Reparación equipo",
            amount: -400,
            time: new Date("07-02-2023"),
          },
          {
            id: 6,
            title: "Movimiento 6",
            description: "Reparación equipo",
            amount: -600,
            time: new Date("07-02-2023"),
          },
          {
            id: 7,
            title: "Movimiento 7",
            description: "Reparación equipo",
            amount: -300,
            time: new Date("07-02-2023"),
          },
          {
            id: 8,
            title: "Movimiento 8",
            description: "Reparación equipo",
            amount: 0,
            time: new Date("07-02-2023"),
          },
          {
            id: 9,
            title: "Movimiento 9",
            description: "Reparación equipo",
            amount: 300,
            time: new Date("03-01-2023"),
          },
          {
            id: 10,
            title: "Movimiento 10",
            description: "Reparación equipo",
            amount: 500,
            time: new Date("03-01-2023"),
          },
        ]
      }
    },
    computed: {
      amounts(){
        const lastDays = this.movements.filter(m => {
          const today = new Date()
          const oldDate = today.setDate(today.getDate() - 30)
          console.log(m.time)
          return m.time > oldDate
        }).map(m => m.amount)

        return lastDays.map((m, i) => {
          const lastMovements = lastDays.slice(0, i)

          return lastMovements.reduce(( suma, movement ) => {
            return suma + movement
          }, 0)
        })
      }
    }
  }
</script>