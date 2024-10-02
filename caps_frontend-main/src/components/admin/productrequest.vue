<template>
<div style="height:1200px;">
  <br><br>
  <v-row>
    <v-col>
      <v-select v-model="selectedOption" :items="options" label="Select Table" style=" position:absolute; right:73px; width:200px;" outlined></v-select>
    </v-col>
  </v-row>
  <v-container style="margin-top:50px; width:940px; margin-left: 350px;font-family: 'Poppins', sans-serif; font-size:13px; ">
      <!-- Pending Orders table -->
      <v-row v-if="selectedOption === 'Pending Orders'">
        <v-col>
          <v-card>
            <v-card-title style="color:#1679AB; ">Pending Orders</v-card-title>
            <!-- Replace with your insert component -->
            <insert @data-saved="getOrder" />
            <v-data-table 
              :headers="headers"
              :items="pendingOrders"
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
                <v-btn @click="approveEvent(item.id)" color="success" small>
                  Approve
                </v-btn>
                <v-btn @click="denyEvent(item.id)" color="error" style="width:105px;margin-top:5px;" small>
                  Deny
                </v-btn>
              </template>
              
              <template v-for="(header, index) in headers" v-slot:[`header.${header.value}`]="{ props }">
                <th :key="index">
                  <span>{{ getHeaderTitle(header.value) }}</span>
                </th>
              </template>
            </v-data-table>
          </v-card>
        </v-col>
      </v-row>
  
      <!-- Approved Orders table -->
      <v-row v-else-if="selectedOption === 'Approved Orders'">
        <v-col>
          <v-card>
            <v-card-title style="color:#1679AB; ">Approved Orders</v-card-title>
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
                <v-btn style="width:100px; margin-bottom:5px;" @click="pendingEvent(item.id)" color="success" small>
                  Undo
                </v-btn>
                <v-btn style="width:100px;" @click="denyEvent(item.id)" color="error" small>
                  Deny
                </v-btn>
              </template>
              <template v-for="(header, index) in headers" v-slot:[`header.${header.value}`]="{ props }">
                <th :key="index">
                  <span>{{ getHeaderTitle(header.value) }}</span>
                </th>
              </template>
            </v-data-table>
          </v-card>
        </v-col>
      </v-row>
  
      <!-- Declined Orders table -->
      <v-row v-else-if="selectedOption === 'Declined Orders'">
        <v-col>
          <v-card>
            <v-card-title style="color:#1679AB; ">Declined Orders</v-card-title>
            <v-data-table
              :headers="headers"
              :items="declinedOrders"
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
                <v-btn style="width:100px; margin-bottom:5px;" @click="pendingEvent(item.id)" color="success" small>
                  Undo
                </v-btn>
                <v-btn style="width:100px;" @click="denyEvent(item.id)" color="error" small>
                  Deny
                </v-btn>
              </template>
              <template v-for="(header, index) in headers" v-slot:[`header.${header.value}`]="{ props }">
                <th :key="index">
                  <span>{{ getHeaderTitle(header.value) }}</span>
                </th>
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
        selectedOption: 'Pending Orders', // Default selected option
        options: ['Pending Orders', 'Approved Orders', 'Declined Orders'], // Dropdown options
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
      pendingOrders() {
        return this.infos.filter(order => order.status !== 'approved' && order.status !== 'denied' && order.status !== 'cancelled' && order.status !== 'recieved' && order.status !== 'delivering' && order.status !== 'cancel' && order.status !== 'cart' && order.status !== 'deleted');
      },
      approvedOrders() {
        return this.infos.filter(order => order.status === 'approved');
      },
      declinedOrders() {
        return this.infos.filter(order => order.status === 'denied');
      }
    },
    methods: {
      showPendingOrders() {
      this.selectedOption = 'pending';
    },
    showApprovedOrders() {
      this.selectedOption = 'approved';
    },
    showDeclinedOrders() {
      this.selectedOption = 'declined';
    },
      async getOrder() {
        try {
          const response = await axios.get('getOrder');
          this.infos = response.data; // Update this.infos instead of this.info
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
  
  async pendingEvent(id) {
    try {
      const response = await axios.post(`/updateOrderStatus/${id}`, {
         status: 'pendingbackpricestock' 
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
  async denyEvent(id) {
    try {
      const response = await axios.post(`/updateOrderStatus/${id}`, { status: 'denied' });
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
  
  </style>
  