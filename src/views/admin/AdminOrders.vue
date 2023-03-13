<template>
    後台的訂單列表
    <table class="table mt-4">
    <thead>
      <tr>
        <th>購買時間</th>
        <th>Email</th>
        <th>購買款項</th>
        <th>應付金額</th>
        <th>是否付款</th>

      </tr>
    </thead>
    <tbody>
      <template v-for="(item, key) in orders" :key="key">
        <tr v-if="orders.length" :class="{ 'text-secondary': !item.is_paid }">
          <td>{{ item.create_at}}</td>
          <td><span v-text="item.user.email" v-if="item.user"></span></td>
          <td>
            <ul class="list-unstyled">
              <li v-for="(product, i) in item.products" :key="i">
                {{ product.product.title }} 數量：{{ product.qty }}
                {{ product.product.unit }}
              </li>
            </ul>
          </td>
          <td class="text-right">{{ item.total }}</td>
          <td>
            <div class="form-check form-switch">
              <input
                class="form-check-input"
                type="checkbox"
                :id="`paidSwitch${item.id}`"
                v-model="item.is_paid"
                @change="updatePaid(item)"
              />
              <label class="form-check-label" :for="`paidSwitch${item.id}`">
                <span v-if="item.is_paid">已付款</span>
                <span v-else>尚未付款</span>
              </label>
            </div>
          </td>
        </tr>
      </template>
    </tbody>
  </table>
</template>
<script>
const { VITE_APP_URL, VITE_APP_PATH } = import.meta.env
export default {
  data () {
    return {
      orders: {},
      isNew: false,
      pagination: {},
      isLoading: false,
      tempOrder: {},
      currentPage: 1
    }
  },
  methods: {
    getOrders () {
      const url = `${VITE_APP_URL}api/${VITE_APP_PATH}/admin/orders`
      this.isLoading = true
      this.$http.get(url).then((res) => {
        this.orders = res.data.orders
        console.log(this.orders)
        this.isLoading = false
      }).catch((error) => {
        this.isLoading = false
        console.log(error)
      })
    }
  },
  mounted () {
    this.getOrders()
  }
}
</script>
