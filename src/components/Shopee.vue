<template>
  <div>
    <div class="hello" >
      <h1>Shopee Case Study</h1>
      <div class="input-wrapper">
        <label> Customer Name: </label>
        <br>
        <input type="text" v-model="customerName" class="checkbox" required>
        <br><br>
      </div>
      <div class="input-wrapper">
        <label>Date of Sale:</label>
        <br>
        <input type="date" v-model="date" class="checkbox" required>
        <br><br>

        <label>Sale Item:</label>
        <br>
        <input type="text" v-model="item" class="checkbox" required>
        <br><br>
      </div>
      <div class="input-wrapper">
        <label>Sale Item Value:</label>
        <br>
        <input type="text" v-model="value" class="checkbox" required>
        <br><br>
      </div>
      <div class="input-wrapper">
        <label>Seller Name</label>
        <br>
        <select v-model="sellerName">
          <option v-for="seller in sellers" :value="seller">
            {{ seller }}
          </option>
        </select>
        <button class="btn btn-primary" type="button" @click="addItem"> Add  </button>
        <br><br>
      </div>
    </div>
    <form id="shopping-list">
      <table class="table table-condensed table-hover">
        <tr>
          <th>Item</th>
          <th>Customer</th>
          <th>Seller</th>
          <th>Date</th>
          <th>Value</th>
        </tr>
        <thread>
        </thread>
        <tr v-for="item in itemsList">
          <td>
            <span v-model="item.item">{{ item.item }}</span>
          </td>
          <td>
            <span>{{ item.customerName }}</span>
          </td>
          <td>
            <span>{{ item.sellerName }}</span>
          </td>
          <td>
            <span>{{ item.date }}</span>
          </td>
          <td>
            <span>{{ item.value }}</span>
          </td>
        </tr>
      </table>
    </form>
  </div>
</template>

<script>
export default {
  name: 'Shopee',
  data () {
    return {
      sellers: ["Seller 1", "Seller 2", "Seller 3", "Seller 4", "Seller 5"],
      item: '',
      customerName: '',
      sellerName: '',
      date: '',
      value: '',
      itemsList: [
        {
          item: "ipad",
          customerName: "Renan",
          sellerName: 'Seller 2',
          date: "24-11-2021",
          value: 34.67
        }
      ]
    }
  },
  methods: {
    addItem() {
      if(this.item == '' || this.customerName == '' || this.sellerName == '' ||
      this.date == '' || this.value == '') {
        alert("The form do not accept any empty field.")
      } else{
        this.itemsList.push({
          item: this.item,
          customerName: this.customerName,
          sellerName: this.sellerName,
          date: this.date,
          value: Number(this.value)
        });
        this.clearAll()
        this.itemsList = this.rearrange()
      }
    },
    clearAll() {
      this.item = '',
        this.customerName = '',
        this.sellerName = '',
        this.date = '',
        this.value = ''
    },
    rearrange() {
      function compare(a,b) {
        if (a.value > b.value)
          return -1;
        if (a.value < b.value)
          return 1;
        return 0;
      }

      return this.itemsList.sort(compare);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#shopping-list-table{
  table-layout: fixed;
  width: 50%;
  vertical-align: middle;
}

.input-wrapper {
  max-width: 400px;
}
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

input {
  width: 80%;
  padding: 14px 20px;
  margin: 8px 0;
  border-radius: 4px;
}

select {
  width: 50%;
  padding: 14px 20px;
  margin: 8px 0;
  border-radius: 4px;
}

body {
  padding: 1%;
  background-color: #abca
}
.hello {
  margin-left: auto;
  margin-right: auto;
  margin-top: 60px;
  max-width: 550px;

}
</style>
