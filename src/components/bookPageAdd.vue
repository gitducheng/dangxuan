<template>
    <div class="video">
        <form action="#" method="post" class="definewidth m20" enctype="multipart/form-data">
        <table class="table table-bordered table-hover m10" style="margin-left:10px;margin-top:3px;">
            <tr>
                <td width="10%" class="tableleft">杂志名称</td>
                <td>
                    <select name="bigTypeId">
                        <option value="0">微众</option>
                    </select>
                </td>
            </tr>
            <tr>
                <td class="tableleft">期数</td>
                <td>
                    <select name="bigTypeId">
                        <option value="1">第一期</option>
                        <option value="2">第二期</option>
                        <option value="3">第三期</option>
                        <option value="4">第四期</option>
                    </select>
                </td>
            </tr>
            <tr>
                <td class="tableleft">文章标题</td>
                <td><input type="text" name="words"/></td>
            </tr>
            <tr>
                <td class="tableleft">文章内容</td>
                <td class="tableleft" >
            
                        <!-- <h1>完整demo</h1> -->
                        <script id="editor" type="text/plain" style="width:1024px;height:400px;offsetWidth:0px"></script>
                 
                    <div id="btns">
                        <div>
                            <!-- <span class="btn btn-success" @click="createEditor()">获得整个html的内容</span >
                            <span class="btn btn-success" @click="getContent()">获得内容</span >  -->
                        </div>
                    </div>
                    <!-- <textarea id="inputProductM" rows="10" cols="50" class="form-control"></textarea> -->
                </td>
        <!--         <td class="tableleft">图片预览</td> -->
        <!--         <td><img name="showimg" id="showimg" src="" style="display:none;" alt="预览图片" /> </td> -->
            </tr>
            
            <tr>
                <td class="tableleft"></td>
                <td>
                    <span style="margin-left:5px;" class="btn btn-primary" @click="addPage">保存</span> &nbsp;&nbsp;<span class="btn btn-success" name="backid" id="backid" @click="returnItem('bookList')">返回列表</span>
                </td>
            </tr>
        </table>
    </form>

  </div>
</template>

<script>
import Axios from 'axios'
export default {
  name: 'bookPageAdd',
  data () {
    return {
      username:"",
      password:"",
      message:''
    }
  },
  methods:{
    returnItem(item){
        this.$emit('choseItem',item)
    },
    editor(){
    //   var ue = UE.getEditor('editor');
    //   this.createEditor();
    },
    getAllHtml(){
        alert(UE.getEditor('editor').getAllHtml())
    },
    getContent(){
         var arr = [];
        arr.push("使用editor.getContent()方法可以获得编辑器的内容");
        arr.push("内容为：");
        arr.push(UE.getEditor('editor').getContent());
        alert(arr.join("\n"));
    },
    createEditor(){
      UE.getEditor('editor')
        
    },
    addPage(){
        Axios.post('/admin/magazine/addArticle',{
            magazine_journal_no:'1',//(期数)
            list_title:'文章添加',//（文章标题）
            list_content:'添加内容',//(文章内容)
            list_writer:'作者'//(文章作者)
        })
        .then(res=>{
            console.log(res.data);
        })
        .catch(err=>{
            console.log(err);
        })
    }
  },
  mounted(){
      this.$nextTick(()=>{
           document.getElementById('right').style.overflowY= 'scroll';
         UE.delEditor('editor');
          this.createEditor();
         
      })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
body {font-size: 20px;
            padding-bottom: 40px;
            background-color:#e9e7ef;
        }
        .sidebar-nav {
            padding: 9px 0;
        }

        @media (max-width: 980px) {
            /* Enable use of floated navbar text */
            .navbar-text.pull-right {
                float: none;
                padding-left: 5px;
                padding-right: 5px;
            }
        }
body{
    font-size: 13px;
}
select, textarea, input[type="text"], input[type="password"], input[type="datetime"], input[type="datetime-local"], input[type="date"], input[type="month"], input[type="time"], input[type="week"], input[type="number"], input[type="email"], input[type="url"], input[type="search"], input[type="tel"], input[type="color"], .uneditable-input {
    padding: 1px;
}

select {
    height: 24px;
}

.radio{
    font-size: 11px;
    margin-bottom: 4px;
}

.nav{
    margin-bottom: 5px;
}

form{
    margin: 0 0 5px;
}

.page{
    text-align: right;margin-right:25px;margin-top:5px;
}

.page a{
    margin-left: 5px;
}

.page .current{
    margin-left: 5px;
    color: red;
}
/*1*/
.table td input[type="checkbox"]{
    padding: 0;
    margin: 0;
}

.table th input[type="checkbox"]{
    padding: 0;
    margin: 0;
}

.table td, .table th{
    padding-top: 8px;
    padding-bottom: 4px;
	line-height:20ppx;
	
}
.table th{
	background-color:#eaeaea;
}
.tableleft{
	text-align:left;
	padding-left:5px;
	background-color:#f5f5f5;

}
.definewidth{
	width:96%;
	margin:auto;		
}

/*2*/
.table2 td input[type="checkbox"]{
    padding: 0;
    margin: 0;
}

.table2 th input[type="checkbox"]{
    padding: 0;
    margin: 0;
}

.table2 td, .table2 th{
    padding-top: 10px;
    padding-bottom: 4px;
	line-height:50ppx;
	
}
.table2 th{
	background-color:#eaeaea;
}
.table2left{
	text-align:center;
	padding-left:10px;
	background-color:#f5f5f5;

}
.definewidth2{
	width:50%;
	margin:auto;
}



.m10{
	margin-top:10px;
}
.m20{
	padding-top:20px;
}
.m30{
	padding-top:50px;
}





/*formValidator�?��֤*/
.onShow,.onFocus,.onError,.onCorrect,.onLoad,.onTime{display:inline-block;display:-moz-inline-stack;zoom:1;*display:inline; vertical-align:middle;	color:#444;line-height:18px;padding:2px 10px 2px 23px; margin-left:10px;_margin-left:5px}
.onShow{background-position:3px -147px;border-color:#40B3FF;color:#959595}
.onFocus{background-position:3px -147px;border-color:#40B3FF;}
.onError{background-position:3px -47px;border-color:#40B3FF; color:red}
.onCorrect{background-position:3px -247px;border-color:#40B3FF;}
.onLamp{background-position:3px -200px}
.onTime{background-position:3px -1356px}
</style>
