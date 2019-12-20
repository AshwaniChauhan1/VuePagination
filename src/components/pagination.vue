<template>
  <div>
    <div>
      <h1>TABLE - PAGINATION</h1>
    </div>
    <table>
      <thead>
        <tr>
          <th v-for="(item,index) in items" :key="index">{{item | capitalize}}</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(row,index) in get_rows()" :key="index">
          <td v-for="(item,index) in items" :key="index">{{row[item]}}</td>
        </tr>
      </tbody>
    </table>
    <div class="pagination">
      <div
        class="number"
        v-for="(i,index) in num_pages()"
        :key="index"
        :class="[i == currentPage ? 'active' : '']"
        @click="change_page(i)"
      >{{i}}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "pagination",
  data() {
    return {
      items: ["id", "name", "phone", "profession"],
      rows: [
        {
          id: 1,
          name: "Chandler Bing",
          phone: "305-917-1301",
          profession: "IT Manager"
        },
        {
          id: 2,
          name: "Ross Geller",
          phone: "210-684-8953",
          profession: "Paleontologist"
        },
        {
          id: 3,
          name: "Rachel Green",
          phone: "765-338-0312",
          profession: "Waitress"
        },
        {
          id: 4,
          name: "Monica Geller",
          phone: "714-541-3336",
          profession: "Head Chef"
        },
        {
          id: 5,
          name: "Jonty Rodes",
          phone: "972-297-6037",
          profession: "Actor"
        },
        {
          id: 6,
          name: "Gary Cristain",
          phone: "330-318-8676",
          profession: "Masseuse"
        },
        {
          id: 7,
          name: "Don Bradman",
          phone: "560-818-9376",
          profession: "Footballer"
        },
        {
          id: 8,
          name: "Viv Richard",
          phone: "790-918-4576",
          profession: "Cricketer"
        },
        {
          id: 9,
          name: "Rickey Ponting",
          phone: "960-378-8376",
          profession: "Engineer"
        },
        {
          id: 10,
          name: "Steve Smith",
          phone: "260-318-8376",
          profession: "Doctor"
        },
        {
          id: 11,
          name: "Andrew Flintof",
          phone: "760-318-8376",
          profession: "wrestler"
        },
        {
          id: 12,
          name: "Steve Waugh",
          phone: "900-388-7076",
          profession: "Lawyer"
        }
      ],
      currentPage: 1,
      elementsPerPage: 5
    };
  },
  methods: {
    num_pages: function() {
      return Math.ceil(this.rows.length / this.elementsPerPage);
    },
    get_rows: function() {
      var start = (this.currentPage - 1) * this.elementsPerPage;
      var end = start + this.elementsPerPage;
      return this.rows.slice(start, end);
    },
    change_page: function(i) {
      this.currentPage = i;
    }
  },
  filters: {
    capitalize: function(str) {
      return str.charAt(0).toUpperCase() + str.slice(1);
    }
  }
};
</script>

<style scoped>
table {
  width: 100%;
  border-collapse: collapse;
}
th,
td {
  padding: 10px 20px;
  border: 1px solid black;
  width:200px;
}
h1 {
  padding: 20px;
}
.pagination {
  font-family: 'Open Sans', sans-serif;
  text-align: center;
  padding: 32px;
}
.number {
  display: inline-block;
  padding: 4px 10px;
  color: #FFF;
  border-radius: 4px;
  background: #717699;
  margin: 0px 5px;
  cursor: pointer;
}
.number:hover, .number.active { 
  background: rgb(42, 159, 189);
}
</style>