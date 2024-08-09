<template>
  <section class="container-fluid py-5 px-5">
    <table class="table table-success table-striped align-middle w-100">
      <thead>
        <tr>
          <th scope="col" style="width: 30%" class="py-3 ps-3 fw-bold">品項</th>
          <th scope="col" style="width: 35%" class="py-3 fw-bold">描述</th>
          <th scope="col" style="width: 15%" class="py-3 fw-bold">價格</th>
          <th scope="col" style="width: 20%" class="py-3 fw-bold">庫存</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in productList" :key="index">
          <td class="py-5 ps-3">{{ item.title }}</td>
          <td>{{ item.describe }}</td>
          <td>{{ item.price }}</td>
          <td>
            <button
              type="button"
              class="btn btn-dark"
              v-bind:class="[item.stock === 0 ? 'btn-outline-danger' : null]"
              v-bind:disabled="item.stock === 1"
              v-on:click="item.stock--"
            >
              <i class="bi bi-dash-lg"></i>
            </button>

            <div style="padding: 12px; display: inline-block; text-align: center">
              {{ item.stock }}
            </div>

            <button type="button" class="btn btn-dark" v-on:click="item.stock++">
              <i class="bi bi-plus-lg"></i>
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </section>
</template>

<style scoped>
* {
  font-size: 32px;
  font-weight: 500;
}
</style>

<script setup>
import { ref } from 'vue'

const productList = ref([
  { title: '珍珠奶茶', describe: '香濃奶茶搭配QQ珍珠', price: 50, stock: 20 },
  { title: '冬瓜檸檬', describe: '清新冬瓜配上新鮮檸檬', price: 55, stock: 34 },
  { title: '翡翠檸檬', describe: '綠茶與檸檬的完美結合', price: 50, stock: 20 },
  { title: '四季春茶', describe: '香醇四季春茶，回甘無比', price: 45, stock: 0 },
  { title: '阿薩姆奶茶', describe: '阿薩姆紅茶搭配香醇鮮奶', price: 50, stock: 25 },
  { title: '檸檬冰茶', describe: '檸檬與冰茶的清新組合', price: 45, stock: 20 },
  { title: '芒果綠茶', describe: '芒果與綠茶的獨特風味', price: 55, stock: 18 },
  { title: '抹茶拿鐵', describe: '抹茶與鮮奶的絕配', price: 60, stock: 20 }
])
</script>
