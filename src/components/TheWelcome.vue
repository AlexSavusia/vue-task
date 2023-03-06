<template>
  <div>
    <div class="header-box">

      <div id="selected-items" class="left-box">
        <div v-if="!selected_items.length" class="name">No items selected</div>
        <div v-for="item in selected_items" :key="item.name" class="selected items">
          <p class="name">{{item.name}}</p>
        </div>
      </div>

      <div id="selected-item" class="right-box">
        <div v-if="!selected_item.length" class="name">No item selected</div>
        <div v-for="item in selected_item" :key="item.name" class="item">
          <p class="selected-name">{{item.name}}</p>
        </div>
      </div>
    </div>

    <div class="body-box">
      <div id="user-items" class="left-body">
        <div class="user items"  v-for="item in users_items" :key="item.name" :id="item.id" @click="addUserItems(item.id)">
          <div class="name">{{item.name}}</div>
        </div>
      </div>

      <div id="choose-items" class="right-body">
        <div class="choose items"  v-for="item in choose_items" :key="item.name" :id="item.id" @click="addChooseItems(item.id)">
          <div class="name">{{item.name}}</div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "dropdown",
  data() {
    return {
      border: "1px solid gray",
      config: {
        disabled: false,
        length: 8
      },
      selected_items: [
      ],
      selected_item: [],
      users_items: [
        {
          "id": 1,
          "name": "Shoes 1"
        },
        {
          "id": 2,
          "name": "Shoes 2"
        },
        {
          "id": 3,
          "name": "Shoes 3"
        },
        {
          "id": 4,
          "name": "Shoes 4"
        },
        {
          "id": 5,
          "name": "T-shirt 1"
        },
        {
          "id": 6,
          "name": "T-shirt 2"
        },
        {
          "id": 7,
          "name": "T-shirt 3"
        },
        {
          "id": 8,
          "name": "T-shirt 4"
        }
      ],
      choose_items: [
        {
          "id": 11,
          "name": "Jacket 1"
        },
        {
          "id": 12,
          "name": "Jacket 2"
        },
        {
          "id": 13,
          "name": "Jacket 3"
        },
        {
          "id": 14,
          "name": "Jacket 4"
        },
        {
          "id": 15,
          "name": "Hoodie 1"
        },
        {
          "id": 16,
          "name": "Hoodie 2"
        },
        {
          "id": 17,
          "name": "Hoodie 3"
        },
        {
          "id": 18,
          "name": "Hoodie 4"
        }
      ]
    };
  },
  components: {},
  computed: {},
  methods: {
    addUserItems(item) {
      for (let u = 0; u < this.selected_items.length; u++) {
        if (item === this.selected_items[u].id) {
          return
        }
      }
      for (let i = 0; i < this.users_items.length; i++) {
        if (item === this.users_items[i].id) {
          this.selected_items.push(this.users_items[i])
        }
      }
    },
    addChooseItems(item) {
      this.selected_item = []
      for (let i = 0; i < this.choose_items.length; i++) {
        if (item === this.choose_items[i].id && !this.selected_item[i]) {
          this.selected_item.push(this.choose_items[i])
        }
      }
    },
  },
};
</script>

<style scoped>
.header-box, .body-box {
  display: flex;
  justify-content: space-between;
  padding: 20px;
}
.left-box, .right-box {
  height: 300px;
  width: 300px;
  border: 5px solid black;
  padding: 20px;
  display: grid;
  grid-template-columns: repeat(auto-fill, 100px);
  grid-template-rows: 50px 50px;
  grid-column-gap: 20px;
  grid-row-gap: 20px;
  justify-items: stretch;
  align-items: stretch;
}

.left-body, .right-body {
  width: 600px;
  height: 800px;
  border: 5px solid black;
  display: grid;
  grid-template-columns: repeat(auto-fill, 122px);
  grid-template-rows: 100px 100px;
  grid-column-gap: 20px;
  grid-row-gap: 20px;
  justify-items: stretch;
  align-items: stretch;
  padding: 20px;
}
.items {
  margin: 0 auto;
  width: 100px;
  height: 100px;
  border: 5px solid black;
}
.name {
  font-size: 16px;
  font-weight: bold;
  text-align: center;
}
.item {
  margin: auto;
  height: 250px;
  width: 250px;
  align-items: center;
  display: flex;
  justify-content: center;
}
.selected {
  height: 50px;
  width: 50px;
}
.selected >.name {
  font-size: 12px;
}
.selected-name {
  font-size: 26px;
  font-weight: bold;
  text-align: center;
  margin: auto;
}
</style>