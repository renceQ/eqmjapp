<template>
  <div style="height: 1000px;">
    <br>
    <v-container style="width: 940px; margin-left: 350px; font-family: 'Poppins', sans-serif; font-size: 13px;">
      <!-- Order List table -->
      <v-row>
        <v-col>
          <v-select v-model="selectedOption" :items="options" label="Select Table" style="position: absolute; right: 73px; width: 200px;" outlined></v-select>
        </v-col>
      </v-row>
      <br><br><br>

      <v-row style="margin-top: 5px;" v-if="selectedOption === 'Order List'">
        <v-col>
          <v-card>
            <v-card-title style="color: #1679AB;">Order List</v-card-title>
            <!-- Replace with your insert component diko pa mapalabas shipping fee at total with shipping fee last nyan -->
            <insert @data-saved="getOrder" />
            <v-data-table 
              :headers="headers"
              :items="approvedOrders"
              item-key="id"
            >
              <template v-slot:[`item.transaction_code`]="{ item }">
                <span>{{ item.transaction_code }}</span>
              </template>
              <template v-slot:[`item.updated_at`]="{ item }">
                <span>{{ item.updated_at }}</span>
              </template>
              <template v-slot:[`item.created_at`]="{ item }">
                <span>{{ item.created_at }}</span>
              </template>
              <template v-slot:[`item.image`]="{ item }">
                <img :src="item.image" alt="Product Image" width="50" height="50">
              </template>
              <template v-slot:[`item.actions`]="{ item }">
                <v-btn style="margin-bottom: 5px;" @click="deliveringEvent(item.id)" color="success" small>
                  Deliver Product
                </v-btn>
                <v-btn style="width: 175px;" @click="openviewdialog(item.id)" color="black" small>
                  <v-icon>mdi-eye</v-icon> View Details
                </v-btn>
              </template>
              <template v-for="(header, index) in headers" v-slot:[`header.${header.value}`]="{ props }">
                <th :key="index">
                  <span>{{ getHeaderTitle(header.value) }}</span>
                </th>
              </template>
              <template v-slot:[`item.totalplusshipping`]="{ item }">
                <span>{{ item.totalplusshipping }}</span>
              </template>
              <template v-slot:[`item.shippingFee`]="{ item }">
                <span>{{ item.shippingFee }}</span>
              </template>
            </v-data-table>
          </v-card>
        </v-col>
      </v-row>

      <!-- On Delivery Orders table -->
      <v-row style="margin-top: 5px;" v-else-if="selectedOption === 'On Delivery Orders'">
        <v-col>
          <v-card>
            <v-card-title style="color: #1679AB;">On Delivery Orders</v-card-title>
            <v-data-table
              :headers="headers"
              :items="deliveringOrders"
              item-key="id"
            >
              <template v-slot:[`item.transaction_code`]="{ item }">
                <span>{{ item.transaction_code }}</span>
              </template>
              <template v-slot:[`item.updated_at`]="{ item }">
                <span>{{ item.updated_at }}</span>
              </template>
              <template v-slot:[`item.created_at`]="{ item }">
                <span>{{ item.created_at }}</span>
              </template>
              <template v-slot:[`item.image`]="{ item }">
                <img :src="item.image" alt="Product Image" width="50" height="50">
              </template>
              <template v-slot:[`item.actions`]="{ item }">
                <v-btn style="width: 157px; margin-bottom: 5px;" @click="approveEvent(item.id)" color="error" small>
                  Undo
                </v-btn>
                <v-btn @click="delivered(item.id)" color="success" small>
                  Item Delivered
                </v-btn>
                <v-btn style="width: 157px; margin-top: 5px;" @click="openviewdialog(item.id)" color="black" small>
                  <v-icon>mdi-eye</v-icon> View Details
                </v-btn>
              </template>
              <template v-for="(header, index) in headers" v-slot:[`header.${header.value}`]="{ props }">
                <th :key="index">
                  <span>{{ getHeaderTitle(header.value) }}</span>
                </th>
              </template>
              <template v-slot:[`item.totalplusshipping`]="{ item }">
                <span>{{ item.totalplusshipping }}</span>
              </template>
              <template v-slot:[`item.shippingFee`]="{ item }">
                <span>{{ item.shippingFee }}</span>
              </template>
            </v-data-table>
          </v-card>
        </v-col>
      </v-row>

      <!-- Delivered Orders table -->
      <v-row style="margin-top: 5px;" v-else-if="selectedOption === 'Delivered Orders'">
        <v-col>
          <v-card>
            <v-card-title style="color: #1679AB;">Delivered Orders</v-card-title>
            <v-data-table
              :headers="headers"
              :items="deliveredOrders"
              item-key="id"
            >
              <template v-slot:[`item.transaction_code`]="{ item }">
                <span>{{ item.transaction_code }}</span>
              </template>
              <template v-slot:[`item.updated_at`]="{ item }">
                <span>{{ item.updated_at }}</span>
              </template>
              <template v-slot:[`item.created_at`]="{ item }">
                <span>{{ item.created_at }}</span>
              </template>
              <template v-slot:[`item.image`]="{ item }">
                <img :src="item.image" alt="Product Image" width="50" height="50">
              </template>
              <template v-slot:[`item.actions`]="{ item }">
                <v-btn style="width: 160px; margin-bottom: 5px;" @click="deliveringEvent(item.id)" color="success" small>
                  Undo
                </v-btn>
                <v-btn @click="openviewdialog(item.id)" color="black" small>
                  <v-icon>mdi-eye</v-icon> View Details
                </v-btn>
              </template>
              <template v-for="(header, index) in headers" v-slot:[`header.${header.value}`]="{ props }">
                <th :key="index">
                  <span>{{ getHeaderTitle(header.value) }}</span>
                </th>
              </template>
              <template v-slot:[`item.totalplusshipping`]="{ item }">
                <span>{{ item.totalplusshipping }}</span>
              </template>
              <template v-slot:[`item.shippingFee`]="{ item }">
                <span>{{ item.shippingFee }}</span>
              </template>
            </v-data-table>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import axios from 'axios'; // Import axios library

export default {
  data() {
    return {
      selectedOption: 'Order List', // Default selected option
      options: ['Order List', 'On Delivery Orders', 'Delivered Orders'], // Dropdown options
      headers: [
        { text: 'Actions', value: 'actions', sortable: false },
        { text: 'Transaction Code', value: 'transaction_code' }, 
        { text: 'Date Updated', value: 'updated_at' }, 
        { text: 'Date Requested', value: 'created_at' }, 
        { text: 'Image', value: 'image' },
        { text: 'Product Name', value: 'prod_name' },
        { text: 'Unit Price', value: 'unit_price' },
        { text: 'Total', value: 'total' },
        { text: 'Size ID', value: 'size_id' },
        { text: 'Quantity', value: 'quantity' },
        { text: 'Address', value: 'address' },
        { text: 'Contact', value: 'contact' },
        { text: 'Other Info', value: 'other_info' },
        { text: 'Customer Name', value: 'customerName' },
        { text: 'Status', value: 'status' },
        { text: 'Total w Shipping', value: 'totalplusshipping' },
        { text: 'Shipping Fee', value: 'shippingFee' },
      ],
      infos: [] // Initialize infos as an empty array
    };
  },
  created() {
    this.getOrder();
  },
  computed: {
    approvedOrders() {
      return this.infos.filter(order => order.status !== 'pending' && order.status !== 'denied' && order.status !== 'delivering' && order.status !== 'recieved' && order.status !== 'cancelled' && order.status !== 'deleted');
    },
    deliveringOrders() {
      return this.infos.filter(order => order.status === 'delivering');
    },
    deliveredOrders() {
      return this.infos.filter(order => order.status === 'recieved');
    }
  },
  methods: {
    async getOrder() {
      try {
        const response = await axios.get('getOrder');
        console.log(response.data); // Log the data to check if the fields are present
        this.infos = response.data;
      } catch (error) {
        console.error(error);
      }
    },

    async approveEvent(id) {
      try {
        const response = await axios.post(`/updateOrderStatus/${id}`, { status: 'approved' });
        if (response.status === 200) {
          this.getOrder(); // Refresh orders after status update
        } else {
          console.error('Error updating order status');
        }
      } catch (error) {
        console.error('Error updating order status:', error);
      }
    },

    async delivered(id) {
      try {
        const response = await axios.post(`/updateOrderStatus/${id}`, { status: 'recieved' });
        if (response.status === 200) {
          this.getOrder(); // Refresh orders after status update
        } else {
          console.error('Error updating order status');
        }
      } catch (error) {
        console.error('Error updating order status:', error);
      }
    },

    async pendingEvent(id) {
      try {
        const response = await axios.post(`/updateOrderStatus/${id}`, { status: 'pending' });
        if (response.status === 200) {
          this.getOrder(); // Refresh orders after status update
        } else {
          console.error('Error updating order status');
        }
      } catch (error) {
        console.error('Error updating order status:', error);
      }
    },

    async deliveringEvent(id) {
      try {
        const response = await axios.post(`/updateOrderStatus/${id}`, { status: 'delivering' });
        if (response.status === 200) {
          this.getOrder(); // Refresh orders after status update
        } else {
          console.error('Error updating order status');
        }
      } catch (error) {
        console.error('Error updating order status:', error);
      }
    },
    async denyEvent(id) {
      try {
        const response = await axios.post(`/updateOrderStatus/${id}`, { 
          status: 'denied',
          reason: 'The Admin declined your order due to some reasons'
        });
        if (response.status === 200) {
          this.getOrder(); // Refresh orders after status update
        } else {
          console.error('Error updating order status');
        }
      } catch (error) {
        console.error('Error updating order status:', error);
      }
    },

    getHeaderTitle(field) {
      const headerTitles = {
        transaction_code: 'Transact Code',
        updated_at: 'Last Updated',
        created_at: 'Date Requested',
        image: 'Image',
        prod_name: 'Product Name',
        unit_price: 'Unit Price',
        total: 'Total Price',
        size_id: 'Size ID',
        quantity: 'Quantity',
        address: 'Address',
        contact: 'Contact',
        other_info: 'Other Info',
        customerName: 'Customer Name',
        status: 'Status',
        totalplusshipping: 'Total w Shipping',
        shippingFee: 'Shipping Fee',
        actions: 'Actions',
       
        // Add other field titles accordingly
      };
      return headerTitles[field] || '';
    },
  },
};
</script>

<style>
/* Add your styles here */
</style>
