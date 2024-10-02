<template>
  <div style="height:1000px;">
  <br><br><br><br><br>
    <div class="table-container" style="font-family: 'Poppins', sans-serif;">
        <h1 style="font-size: 25px; color:#1679AB;">Product History: {{ productId }}</h1>
        <button @click="downloadPDF" style="position:absolute; background-color:#C51605; border-radius:3px; width:200px; color:white; margin-left:59.1%;  margin-top:-90px; margin-bottom:3%;" class="neumorphic-button">
          Download as PDF  <i style="color:white;" class="fas fa-file-pdf"></i>
        </button>
        <insert @data-saved="getAuditRecords" />
        <table class="product-table" style="font-family: 'Poppins', sans-serif;">
        <thead>
          <tr>
            <th>Image</th>
            <th>Category ID</th>
            <th>Product Name</th>
            <th>Price</th>
            <th>Unit Price</th>
            <th>Size ID</th>
            <th>UPC</th>
            <th>Barcode Image</th>
            <th>Created At</th>
            <th>Updated At</th>
            <th>Product Description</th>
            <th>Type</th>
            <th>Current Stock</th>
            <th>Old Stock</th>
          </tr>
        </thead>
        <tbody>
            <tr v-for="auditRecord in auditRecords" :key="auditRecord.id">
            <td v-if="auditRecord.image">
                <img :src="auditRecord.image" alt="image" class="img-fluid" style="max-width: 100px; max-height:100px;">
              </td>
            <td>{{ getCategoryName(auditRecord.category_id) }}</td>
            <td>{{ auditRecord.prod_name }}</td>
            <td>{{ auditRecord.price }}</td>
            <td>{{ auditRecord.unit_price }}</td>
            <td>{{ getSizeName(auditRecord.size_id) }}</td>
            <td>{{ auditRecord.UPC }}</td>
            <td v-if="auditRecord.barcode_image">
              <img :src="auditRecord.barcode_image" alt="image" class="img-fluid" style="max-width: 100px; max-height:100px;">
            </td>
            <td>{{ auditRecord.created_at }}</td>
            <td>{{ auditRecord.updated_at }}</td>
            <td>{{ auditRecord.product_description }}</td>
            <td>{{ auditRecord.type }}</td>
            <td>{{ auditRecord.stock }}</td>
            <td>{{ auditRecord.old_stock }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
        id: "",
        image: null,
        category_id: "",
        prod_name: "",
        stock: "",
        price: "",
        unit_price: "",
        size_id: "",
        UPC: "",
        barcode_image: null,
        created_at: "",
        updated_at: "",
        product_description: "",
        type: "",
        old_stock:"",
      products: [],
      categories: [],
      sizes: [],
      selectedProductId: null,
      productId: '',
      auditRecords: [],
      }
  },
  created() {
   
    this.productId = this.$route.params.productId; // Get the productId from the route

if (this.productId) {
  this.getAuditRecords(this.productId); // Fetch audit records based on productId
}
  },
  methods: {
    downloadPDF() {
    const docDefinition = {
      pageSize: 'A4',
      pageOrientation: 'landscape',
      content: [
        {
          text: 'QMJ ENTERPRISE EVENT MANAGEMENT AND CREATIVE SERVICES',
          style: 'title',
          alignment: 'center'
        },
        {
          text: 'Generated Report for sales of products.',
          style: 'subtitle',
          alignment: 'center'
        },
        {
          style: 'tableExample',
          table: {
            headerRows: 1,
            widths: ['auto', 'auto', 'auto', 'auto', 'auto', 'auto', 'auto', 'auto', 'auto', 'auto', 'auto', 'auto', 'auto', 'auto'],
            body: [
              [
               
                { text: 'Category ID', style: 'tableHeader' },
                { text: 'Product Name', style: 'tableHeader' },
                { text: 'Price', style: 'tableHeader' },
                { text: 'Unit Price', style: 'tableHeader' },
                { text: 'Size ID', style: 'tableHeader' },
                { text: 'UPC', style: 'tableHeader' },
                // { text: 'Barcode Image', style: 'tableHeader' },
                { text: 'Created At', style: 'tableHeader' },
                { text: 'Updated At', style: 'tableHeader' },
                { text: 'Product Description', style: 'tableHeader' },
                { text: 'Type', style: 'tableHeader' },
                { text: 'Current Stock', style: 'tableHeader' },
                { text: 'Old Stock', style: 'tableHeader' },
              ],
              ...this.auditRecords.map(record => [
                
                { text: this.getCategoryName(record.category_id), fontSize: 8 },
                { text: record.prod_name, fontSize: 8 },
                { text: record.price, fontSize: 8 },
                { text: record.unit_price, fontSize: 8 },
                { text: this.getSizeName(record.size_id), fontSize: 8 },
                { text: record.UPC, fontSize: 8 },
                // { image: record.barcode_image ? record.barcode_image : '', width: 30, height: 30 },
                { text: record.created_at, fontSize: 8 },
                { text: record.updated_at, fontSize: 8 },
                { text: record.product_description, fontSize: 8 },
                { text: record.type, fontSize: 8 },
                { text: record.stock, fontSize: 8 },
                { text: record.old_stock, fontSize: 8 },
              ])
            ]
          },
          layout: {
            paddingLeft: function(i, node) { return 4; },
            paddingRight: function(i, node) { return 4; },
            paddingTop: function(i, node) { return 2; },
            paddingBottom: function(i, node) { return 2; }
          }
        }
      ],
      styles: {
        title: {
          fontSize: 18,
          bold: true,
          marginBottom: 5
        },
        subtitle: {
          fontSize: 12,
          marginBottom: 10
        },
        tableHeader: {
          bold: true,
          fontSize: 10,
          color: 'black'
        }
      }
    };

    pdfMake.createPdf(docDefinition).download(`Product_History_${this.productId}.pdf`);
  },
    async getAuditRecords(productId) {
      try {
        const response = await axios.get(`getaudith/${productId}`);
        this.auditRecords = response.data; // Update auditRecords with fetched data
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
    getCategoryName(categoryId) {
      const category = this.categories.find(category => category.id === categoryId);
      return category ? category.category_name : 'Unknown';
    },async fetchCategories() {
      try {
        const response = await axios.get("getcat");
        this.categories = response.data; // Assuming response.data contains the categories array
      } catch (error) {
        console.error(error);
      }
    },
    async fetchsizes() {
      try {
        const response = await axios.get("getsize");
        this.sizes = response.data;
      } catch (error) {
        console.error(error);
      }
    },
    async fetchCategories() {
      try {
        const response = await axios.get("getcat");
        this.categories = response.data; // Assuming response.data contains the categories array
      } catch (error) {
        console.error(error);
      }
    },
    async fetchsizes() {
      try {
        const response = await axios.get("getsize");
        this.sizes = response.data;
      } catch (error) {
        console.error(error);
      }
    },
  },
  
   
    mounted() {
    this.fetchCategories();
    this.fetchsizes();
  },
};
</script>
  
<style >
/* Add styles to the table container */
.table-container {
  width: 1000px;
  margin-right: 40px;
  font-size: 10px; /* Adjust the font size as needed */
}

/* Add styles to the table */
.product-table {
  width: 100%;
  border-collapse: collapse;
  font-family: Arial, sans-serif;
}

.product-table th,
.product-table td {
  border: 1px solid #ddd;
  padding: 4px; /* Adjust cell padding */
  text-align: left;
  font-size: 10px; /* Adjust the font size as needed */
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

/* Align the table to the right */
@media (min-width: 768px) {
  .table-container {
    float: right;
    margin-left: 20px; /* Adjust margin as needed */
  }
}
</style>
