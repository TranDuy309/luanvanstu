<template>
  <div class="content">
    <div class="container-fluid">
      <div class="row">
        <div class="col-xl-3 col-md-6"><router-link to="/quanlyuser/khachhang">
          <stats-card>
            <div slot="header" class="icon-warning">
              <i class="nc-icon nc-circle-09 text-warning"></i>
            </div>
            <div slot="content">
              <p class="card-category">Khách hàng</p>
              <h4 class="card-title">+15K</h4>
            </div>
            <div slot="footer">
              <i class="fa fa-refresh"></i>Cập nhật
            </div>
          </stats-card>
          </router-link>
        </div>

        <div class="col-xl-3 col-md-6"><router-link to="/quanlyuser/nhanvien">
          <stats-card>
            <div slot="header" class="icon-success">
              <i class="nc-icon nc-badge text-success"></i>
            </div>
            <div slot="content">
              <p class="card-category">Nhân viên</p>
              <h4 class="card-title">+200</h4>
            </div>
            <div slot="footer">
              <i class="fa fa-refresh"></i>Cập nhật
            </div>
          </stats-card>
          </router-link>
        </div>

        <div class="col-xl-3 col-md-6"><router-link to="/quanlysanpham/sanpham">
          <stats-card>
            <div slot="header" class="icon-danger">
              <i class="nc-icon nc-app text-danger"></i>
            </div>
            <div slot="content">
              <p class="card-category">Sản phẩm</p>
              <h4 class="card-title">+100</h4>
            </div>
            <div slot="footer">
              <i class="fa fa-refresh"></i>Cập nhật
            </div>
          </stats-card>
          </router-link>
        </div>

        <div class="col-xl-3 col-md-6"><router-link to="/quanlydonhang/donhang">
          <stats-card>
            <div slot="header" class="icon-info">
              <i class="nc-icon nc-cart-simple text-primary"></i>
            </div>
            <div slot="content">
              <p class="card-category">Đơn hàng</p>
              <h4 class="card-title">+150</h4>
            </div>
            <div slot="footer">
              <i class="fa fa-refresh"></i>Cập nhật
            </div>
          </stats-card>
          </router-link>
        </div>

      </div>
      <div class="row">
        <div class="col-md-7">
          <chart-card :chart-data="lineChart.data"
                      :chart-options="lineChart.options"
                      :responsive-options="lineChart.responsiveOptions">
            <template slot="header">
              <h4 class="card-title">Tương tác</h4>
              <p class="card-category">Trong tuần</p>
            </template>
            <template slot="footer">
              <div class="legend">
                <i class="fa fa-circle text-info"></i> Xem
                <i class="fa fa-circle text-danger"></i> Yêu thích
                <i class="fa fa-circle text-warning"></i> Bình luận
              </div>
              <hr>
              <div class="stats">
                <i class="fa fa-history"></i> Cập nhật
              </div>
            </template>
          </chart-card>
        </div>

       <div class="col-md-5">
          <chart-card
            :chart-data="barChart.data"
            :chart-options="barChart.options"
            :chart-responsive-options="barChart.responsiveOptions"
            chart-type="Bar">
            <template slot="header">
              <h4 class="card-title">Doanh thu</h4>
              <p class="card-category">Tất cả sản phẩm</p>
            </template>
            <template slot="footer">
              <div class="legend">
                <i class="fa fa-circle text-info"></i> Tổng bán
                <i class="fa fa-circle text-danger"></i> Tổng nhập
              </div>
              <hr>
              <div class="stats">
              <i class="fa fa-history"></i> Cập nhật
              </div>
            </template>
          </chart-card>
        </div>
      </div>

      
    </div>
  </div>
</template>
<script>
  import ChartCard from 'src/components/Cards/ChartCard.vue'
  import StatsCard from 'src/components/Cards/StatsCard.vue'


  export default {
    components: {
    
      ChartCard,
      StatsCard
    },
    data () {
      return {
        editTooltip: 'Edit Task',
        deleteTooltip: 'Remove',
        pieChart: {
          data: {
          
            series: [40, 20, 40]
          }
        },
        lineChart: {
          data: {
            labels: ['09:00', '10:00', '11:00', '12:00', '19:00', '20:00', '21:00', '22:00'],
            series: [
              [287, 385, 490, 492, 554, 586, 698, 695],
              [67, 152, 143, 240, 287, 335, 435, 437],
              [23, 113, 67, 108, 190, 239, 307, 308]
            ]
          },
          options: {
            low: 0,
            high: 800,
            showArea: false,
            height: '245px',
            axisX: {
              showGrid: false
            },
            lineSmooth: true,
            showLine: true,
            showPoint: true,
            fullWidth: true,
            chartPadding: {
              right: 50
            }
          },
          responsiveOptions: [
            ['screen and (max-width: 640px)', {
              axisX: {
                labelInterpolationFnc (value) {
                  return value[0]
                }
              }
            }]
          ]
        },
        barChart: {
          data: {
            labels: ['1', '2', '3', '4', '5', '6', '7', '8', '9', '10', '11', '12'],
            series: [
              [542, 443, 320, 780, 553, 453, 326, 434, 568, 610, 756, 895],
              [412, 243, 280, 580, 453, 353, 300, 364, 368, 410, 636, 695]
            ]
          },
          options: {
            seriesBarDistance: 10,
            axisX: {
              showGrid: false
            },
            height: '245px'
          },
          responsiveOptions: [
            ['screen and (max-width: 640px)', {
              seriesBarDistance: 5,
              axisX: {
                labelInterpolationFnc (value) {
                  return value[0]
                }
              }
            }]
          ]
        },
       
      }
    }
  }
</script>
<style>

</style>
