<template>
  <div class="user-container">
    <el-row>
      <el-col :xs="24" :lg="12">
        <el-card class="box-card">
          <div slot="header" class="clearfix">
            <span>用户信息</span>
          </div>
          <div>
            <div style="float: left; margin-right: 10px;">
              <img :src="avatar" width="70px" style="border-radius: 70px;"/>
            </div>
            <div style="">
              <p>账号：{{name}} </p>
              <p>用户名：{{nickName}} </p>
              <p><el-tag size="medium" :type="statusType">{{statusLabel}}</el-tag></p>
            </div>
          </div>
        </el-card>
      </el-col>
      <el-col :xs="24" :lg="12" v-show="status == 1">
        <el-card class="box-card">
          <div slot="header" class="clearfix">
            <span>专属二维码</span>
          </div>
          <div>
            <qrcode :val="qrcodeUrl" :size="100"> </qrcode>
          </div>
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>

<script>

import { mapGetters } from 'vuex'
import qrcode from '@/components/Qrcode'

export default {
  name: 'user',
  data() {
    return {
    }
  },

  components: {
    qrcode
  },

  computed: {
    ...mapGetters([
      'name',
      'nickName',
      'avatar',
      'status',
      'statusLabel',
      'qrcodeUrl'
    ]),
    statusType: function() {
      return this.status === 1 ? 'success' : 'danger'
    }
  },

  created() {

  },

  methods: {

  }

}
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
.user {
  &-container {
    margin: 10px;
  }
  &-text {
    font-size: 30px;
    line-height: 46px;
  }
}
.box-card {
  margin: 10px
}

.idcard-uploader {
    width: 200px;
    height: 300px;
    border: 1px dashed #8c939d;
    border-radius: 6px;
    cursor: pointer;
    position: relative;
    overflow: hidden;
}

.idcard-uploader:hover {
  border-color: #409EFF;
}

.idcard-uploader-icon {
  font-size: 32px;
  color: #8c939d;
  width: 200px;
  height: 300px;
  line-height: 300px;
  text-align: center;
}

.idcard {
  width: 200px;
  height: 300px;
  display: block;
}

.error-msg {
  color: #f56c6c;
  font-size: 12px;
  line-height: 1;
  padding: 4px;
  left: 0;
}
</style>
