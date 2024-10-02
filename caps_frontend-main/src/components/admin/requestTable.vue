<template>
    <div class="clearfix"></div>
    <div class="row" style="margin-left: 300px; margin-right: 20px;">
      <div class="col-md-12 col-sm-12">
        <div class="x_panel">
          <div class="x_title">
            <h2>List of Booked</h2>
            <ul class="nav navbar-right panel_toolbox">
              <li><a class="collapse-link"><i class="fa fa-chevron-up"></i></a></li>
              <li class="dropdown">
                <a href="#" class="dropdown-toggle" data-toggle="dropdown" role="button" aria-expanded="false"><i class="fa fa-wrench"></i></a>
                <div class="dropdown-menu" aria-labelledby="dropdownMenuButton">
                  <a class="dropdown-item" href="#">Settings 1</a>
                  <a class="dropdown-item" href="#">Settings 2</a>
                </div>
              </li>
              <li><a class="close-link"><i class="fa fa-close"></i></a></li>
            </ul>
            <div class="clearfix"></div>
          </div>


          <div class="x_content">
            <div class="row">
              <div class="col-sm-12">
                <div class="card-box table-responsive">
                    <insert @data-saved="getInfo" />
                  <table id="datatable-responsive" class="table table-bordered table-striped dt-responsive nowrap" cellspacing="0" width="80%" style="margin: 0 auto;">
                    <thead>
                      <tr>
                        <th>TRACK CODE</th>
                        <th>FIRSTNAME</th>
                        <th>MIDDLENAME</th>
                        <th>LASTNAME</th>
                        <th>EMAIL</th>
                        <th>ACTIONS</th>
                      </tr>
                    </thead>
                    <tbody>
                      <tr v-for="info in info">
                        <td>{{ info.trackcode}}</td>
                        <td>{{ info.firstname}}</td>
                        <td>{{ info.middlename}}</td>
                        <td>{{ info.lastname}}</td>
                        <td>{{ info.email}}</td>
                        <td>
                          <a href="#" class="btn btn-info btn-sm"> <i class="fa fa-eye-slash"></i> VIEW</a>
                          <a href="#" data-id="1" class="btn btn-success btn-sm edit"><i class="fa fa-edit"></i> EDIT</a>
                          <button class="btn btn-danger btn-sm" @click="deleteRecord(info.id)">Delete</button>
                        </td>
                      </tr>
                    </tbody>
                  </table>
                </div>
              </div>
            </div>
          </div>


          
        </div>
      </div>
    </div>
</template>

<script>
import axios from 'axios'

export default{
    components:{

    },
    data(){
        return{
            info:[],
        }
    },
    created(){
        this.getInfo();
    },
    methods:{
        async getInfo(){
            try {
                const inf = await axios.get('getData');
                this.info = inf.data;
            } 
            catch (error) {
                console.log(error);
            }
        }
    }
}
</script>

<style>

</style>