<template>
  <div class="container">
    <img src="../../assets/v2-a47051e92cf74930bedd7469978e6c08_hd.png" width="128px" height="81px" />
    <el-card class="box">
      <el-tabs v-model="activeName" @tab-click="handleClick">
        <el-tab-pane label="免密码登录" name="first" style="margin-top:15px">
          <el-form ref="loginForm" status-icon :model="loginForm" :rules="loginRules">
            <el-form-item prop="mobile">
              <el-input v-model="loginForm.mobile" placeholder="手机号"></el-input>
            </el-form-item>
            <el-form-item prop="code">
              <el-input
                v-model="loginForm.code"
                placeholder="输入6位短信验证码"
              ></el-input>
              <font size="2"><a class="inputline" href="#">获取短信验证码</a></font>
            </el-form-item>
            <el-link type="info" style="float: right;bottom:15px;">接收语音验证码</el-link>
          </el-form>
        </el-tab-pane>
          <el-tab-pane label="密码登录" name="second" style="margin-top:21px">
          <el-input v-model="input" placeholder="手机号或邮箱" style="height:60px"></el-input>
          <el-input v-model="input" placeholder="密码">
          </el-input>
          <el-button type="text" style="float: left;">海外手机号登录
          </el-button>
           <el-link type="info" style="float: right;top:10px;">忘记密码？</el-link>
        </el-tab-pane>
         <el-button type="primary" class="nav_1">注册/登录</el-button>
         <el-footer>
           <span>未注册手机验证后自动登录</span>
           <br>
           <span>注册即代表同意</span>
           <el-link type="info">《知乎协议》</el-link>
           <el-link type="info">《隐私协议》</el-link>
           <a href="#" style="color: blue;">注册机构号</a>
         </el-footer>
      </el-tabs>
    </el-card>
    <el-card class="box_1">
       <el-link type="info">社交账号登录</el-link>
       <a href="#">微信</a>
       <a href="#">QQ</a>
       <a href="#">微博</a>
      <span></span>
    </el-card>
    <el-card class="box_2">
       <el-link type="primary">下载知乎  App</el-link>
    </el-card>
       <div id="content_bottom">
        <div>
            <a href="#">知乎专栏</a>
            <a href="#">圆桌</a>
            <a href="#">发现</a>
            <a href="#">联系我们</a>
            <a href="#">来知乎工作</a>
            <a href="#">注册机构号</a>
        </div>
        <div>
            <span>© 2019 知乎</span>
            <a href="#">京 ICP 证 110745 号</a>
            <a href="#">京公网安备 11010802010035 号</a>
            <a href="#">出版物经营许可证</a>
        </div>
        <div>
            <a href="#">侵权举报</a>
            <a href="#">网上有害信息举报专区</a>
            <a href="#">儿童色情信息举报专区</a>
            <span>违法和不良信息举报：010-82716601</span>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    // 校验手机号的函数
    const checkMobile = (rule, value, callback) => {
      // 通过校验逻辑判断成功失败
      // 手机号格式：1开头 第二位3-9 9个数字结尾
      if (/^1[3-9]\d{9}$/.test(value)) {
        callback()
      } else {
        callback(new Error('手机号格式不对'))
      }
    }
    return {
      loginForm: {
      },
      activeName: 'first',
      loginRules: {
        mobile: [
          // type: date|email|url  支持  不支持手机号
          { required: true, message: '请输入手机号', trigger: 'blur' },
          { validator: checkMobile, trigger: 'blur' }
        ],
        code: [
          { required: true, message: '输入6位短信验证码', trigger: 'blur' },
          { len: 6, message: '请输入短信验证码', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {}
}
</script>

<style scoped lang='less'>
.container {
    width: 100%;
    height: 100%;
    background: url(../../assets/sign_bg.db29b0fb.png);
    background-size: cover;
    position: absolute;
    left: 0;
    top: 0;
    background-color: #b8e5f8;
    text-align: center;
    overflow: auto;
  }
  .container img {
    margin-top: 30px;
  }
  .box {
    width: 400px;
    height: 380px;
    position: absolute;
    left: 50%;
    top: 42%;
    transform: translate(-50%, -50%);
    margin-top: 30px;
    border:none;
  }
  .box_1 {
    width: 400px;
    height: 55px;
    position: absolute;
    left: 50%;
    top: 80%;
    transform: translate(-50%, -50%);
    .el-link{
      float: left;
    }
    a{
      float: right;
      color: #8590a6;
      text-decoration: none;
      margin-right: 30px;
    }
  }
  .box_2 {
    width: 400px;
    height: 40px;
    position: absolute;
    left: 50%;
    top: 90%;
    transform: translate(-50%, -50%);
  }
  .box_2 /deep/ .el-card__body{
       padding: 10px;
    }
  .nav_1{
      width: 100%;
      margin-top: 10px;
  }
  .el-footer{
      padding: 12px;
      color: grey;
      font-size: 13px;
      background-color: #f6f6f6;
      margin-top: 34px;
      span{
        float: left;
      }
      .el-link{
        float: left;
      }
      a{
        text-decoration: none;
      }
  }
  .el-footer /deep/ .el-card__body{
    padding: 0;
  }
      #content_bottom {
          text-align: center;
          margin-top: 38%;
          font-size: 12px;
          color: #fff;
      }
     #content_bottom a:hover {
          text-decoration: underline;
      }
     #content_bottom img {
          width: 16px;
      }
    #content_bottom a {
          color: #fff;
          text-decoration: none;
      }
    #content_bottom div {
          margin: 8px;
      }
     #content_bottom div *:after {
          content: ' · '
      }
    #content_bottom div *:last-child:after {
          content: ' ';
      }
      .qqq{
        border:none;
      }
      .box /deep/ .el-input__inner {
      border: none;
      border-bottom: 1px solid #ebebeb;
    }
     .box /deep/ .el-tabs__nav-wrap::after {
       height: 3px;
       background: white;
     }
     .box /deep/ .el-tabs__item{
       font-size: 16px;
       color: #303133;
       font-weight: 700;
     }
     .inputline{
          position: absolute;
          right: 0;
          cursor: pointer;
          font-size: 14px;
          text-decoration: none;
          color: #175199;
      }
</style>
