<template>
  <div style="height:1000px;">
  <br><br><br><br><br>
  <div class="table-container" style="font-family: 'Poppins', sans-serif;">
    <h1 style="font-size: 25px; color:#1679AB;">Sales ID: {{ productId }}</h1>
    <button @click="downloadPDF" style="position:absolute; background-color:#C51605; border-radius:3px; width:200px; color:white; margin-left:59.1%;  margin-top:-90px; margin-bottom:3%;" class="neumorphic-button">
      Download as PDF  <i style="color:white;" class="fas fa-file-pdf"></i>
    </button>
    <insert @data-saved="getSalesRecord" />
    <table style="font-family: 'Poppins', sans-serif;" class="product-table">
      <thead>
        <tr>
          <th style="width: 10%;">Product Name</th>
          <th style="width: 10%;">Image</th>
          <th style="width: 5%;">Unit Price</th>
          <th style="width: 8%;">Total Price</th>
          <th style="width: 8%;">Price w Shipping</th>
          <th style="width: 8%;">Shipping Fee</th>
          <th style="width: 5%;">Size ID</th>
          <th style="width: 5%;">Quantity</th>
          <th style="width: 20%;">Address</th>
          <th style="width: 10%;">Contact</th>
          <th style="width: 10%;">Other Info</th>
          <th style="width: 12%;">Customer Name</th>
          <th style="width: 5%;">Status</th>
          <th style="width: 10%;">Transaction Code</th>
          <th style="width: 10%;">Type</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="salesRecord in salesRecords" :key="salesRecord.id">
          <td>{{ salesRecord.prod_name }}</td>
          <td v-if="salesRecord.image">
            <img :src="salesRecord.image" alt="image" class="img-fluid" style="max-width: 100px; max-height:100px;">
          </td>
          <td>{{ salesRecord.unit_price }}</td>
          <td>{{ salesRecord.total }}</td>
          <td>{{ salesRecord.totalplusshipping }}</td>
          <td>{{ salesRecord.shippingFee }}</td>
          <td>{{ getSizeName(salesRecord.size_id) }}</td>
          <td>{{ salesRecord.quantity }}</td>
          <td>{{ salesRecord.address }}</td>
          <td>{{ salesRecord.contact }}</td>
          <td>{{ salesRecord.other_info }}</td>
          <td>{{ salesRecord.customerName }}</td>
          <td>{{ salesRecord.status }}</td>
          <td>{{ salesRecord.transaction_code }}</td>
          <td>{{ salesRecord.type }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</div>
</template>

<script>
import axios from 'axios';
import pdfMake from 'pdfmake/build/pdfmake';
import pdfFonts from 'pdfmake/build/vfs_fonts';

pdfMake.vfs = pdfFonts.pdfMake.vfs;

export default {
  data() {
    return {
      id: "",
      image: null,
      quantity: "",
      prod_name: "",
      stock: "",
      address: "",
      unit_price: "",
      size_id: "",
      contact: "",
      other_info: "",
      customerName: "",
      status: "",
      product_id: "",
      old_stock:"",
      transaction_code: "",
      type: "",
      total: "",
      totalplusshipping: "",
      shippingFee: "",
      products: [],
      categories: [],
      sizes: [],
      selectedProductId: null,
      productId: '',
      salesRecords: [],
    };
  },
  created() {
    this.productId = this.$route.params.productId;
    if (this.productId) {
      this.getSalesRecord(this.productId);
    }
  },
  methods: {
    async getSalesRecord(productId) {
      try {
        const response = await axios.get(`getsales/${productId}`);
        this.salesRecords = response.data;
      } catch (error) {
        console.error(error);
      }
    },
    async getCategories() {
      try {
        const response = await axios.get('getcat');
        this.categories = response.data;
      } catch (error) {
        console.log(error);
      }
    },
    async getItemSizes() {
      try {
        const response = await axios.get('getsize');
        this.sizes = response.data;
      } catch (error) {
        console.log(error);
      }
    },
    getSizeName(sizeId) {
      const size = this.sizes.find(size => size.size_id === sizeId);
      return size ? size.item_size : 'Unknown';
    },
    async downloadPDF() {
  const data = [
    [
      { text: 'Product Name', style: 'tableHeader' },
      { text: 'Unit Price', style: 'tableHeader' },
      { text: 'Total Price', style: 'tableHeader' },
      { text: 'Size ID', style: 'tableHeader' },
      { text: 'Quantity', style: 'tableHeader' },
      { text: 'Address', style: 'tableHeader' },
      { text: 'Contact', style: 'tableHeader' },
      { text: 'Other Info', style: 'tableHeader' },
      { text: 'Customer Name', style: 'tableHeader' },
      { text: 'Status', style: 'tableHeader' },
      { text: 'Transaction Code', style: 'tableHeader' },
      { text: 'Type', style: 'tableHeader' },
    ]
  ];

  this.salesRecords.forEach(record => {
    data.push([
      { text: record.prod_name, style: 'tableData' },
      { text: record.unit_price, style: 'tableData' },
      { text: record.total, style: 'tableData' },
      { text: this.getSizeName(record.size_id), style: 'tableData' },
      { text: record.quantity, style: 'tableData' },
      { text: record.address, style: 'tableData' },
      { text: record.contact, style: 'tableData' },
      { text: record.other_info, style: 'tableData' },
      { text: record.customerName, style: 'tableData' },
      { text: record.status, style: 'tableData' },
      { text: record.transaction_code, style: 'tableData' },
      { text: record.type, style: 'tableData' },
    ]);
  });

  const documentContent = [
    {
      text: 'QMJ ENTERPRISE EVENT MANAGEMENT AND CREATIVE SERVICES',
      style: 'title'
    },
    {
      text: 'Generated Report for sales of products.',
      style: 'subtitle'
    },
    {
      table: {
        headerRows: 1,
        widths: [60, 50, 50, 40, 40, 80, 60, 80, 80, 50, 60, 40], // Adjust column widths to be more compact
        body: data
      }
    }
  ];

  const styles = {
    title: { fontSize: 14, bold: true, alignment: 'center', margin: [0, 10] }, // Slightly smaller title
    subtitle: { fontSize: 10, italic: true, alignment: 'center', margin: [0, 5] }, // Slightly smaller subtitle
    tableHeader: { bold: true, fontSize: 10, color: 'black' }, // Smaller table headers
    tableData: { fontSize: 8 } // Smaller table data
  };

  const docDefinition = {
    content: documentContent,
    styles: styles
  };

  const pdfDocGenerator = pdfMake.createPdf(docDefinition);
  pdfDocGenerator.download('sales_report.pdf');
}

  },
  mounted() {
    this.getCategories();
    this.getItemSizes();
  }
};
</script>

<style>
.table-container {
  width: 1000px;
  margin-right: 40px;
  font-size: 12px;
}

.product-table {
  width: 100%;
  border-collapse: collapse;
  font-family: Arial, sans-serif;
}

.product-table th,
.product-table td {
  border: 1px solid #ddd;
  padding: 6px;
  text-align: left;
}

.product-table th {
  background-color: #f2f2f2;
  font-weight: bold;
}

.product-table tbody tr:nth-child(even) {
  background-color: #f9f9f9;
}

.product-table tbody tr:hover {
  background-color: #e9e9e9;
}

@media (min-width: 768px) {
  .table-container {
    float: right;
    margin-left: 20px;
  }
}
</style>
