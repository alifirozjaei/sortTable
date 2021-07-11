<template>
  <div class="columns">
    <div class="table-container column is-6 is-offset-3">
      <table
        class="table is-bordered is-striped is-narrow is-hoverable is-fullwidth"
      >
        <thead>
          <tr>
            <th @click="sortByString">String</th>
            <th @click="sortByNumber">Number</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(item, index) in items" :key="index">
            <td>{{ item.str }}</td>
            <td>{{ item.num }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>

export default {
  name: "App",
  data: () => ({
    items: [
      { str: "One", num: 1 },
      { str: "Four", num: 4 },
      { str: "five", num: 5 },
      { str: "Two", num: 2 },
      { str: "three", num: 3 },
    ],
    descNumber: false,
    descString: false,
  }),
  // end data

  methods: {
    sortByNumber() {
      this.items.sort((a, b) => {
        if (this.descNumber) {
          return a.num - b.num;
        } else {
          return b.num - a.num;
        }
      });
      this.descNumber = !this.descNumber;
    },

    sortByString() {
      this.items.sort((a, b) => {
        if (this.descString) {
          if (a.str.toUpperCase() < b.str.toUpperCase()) return -1;
          else if (a.str.toUpperCase() > b.str.toUpperCase()) return 1;
          else return 0;
        } else {
          if (a.str.toUpperCase() < b.str.toUpperCase()) return +1;
          else if (a.str.toUpperCase() > b.str.toUpperCase()) return -1;
          else return 0;
        }
      });
      this.descString = !this.descString;
    },
  },
};
</script>
