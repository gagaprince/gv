# gv

简介：前端mvvm类库 致敬vue 用法和vue相似

#### 使用方法

1. npm install
2. gulp 编辑调试
3. gulp publish 打包测试
4. gulp build 打包成min文件
5. 引入到html中去

#### 使用方法
> 引入gv.min.js文件

    new GV({
          el:"test",
          data:function(){
              return {
                  name:"王子冬",
                  sex:"男",
                  imgLink:"http://t2.27270.com/uploads/tu/201612/98/st93.png",
                  mum:{
                      name:"美女",
                      sex:"girl",
                      age:25
                  },
                  children:[
                      {
                          name:"gaga",
                          age:20
                      },
                      {
                          name:"prince",
                          age:40
                      }
                  ]
              }
          },
          methods:{
              clickMe:function(e){
                  console.log(this);
                  console.log(e);
              }
          }
      });

    setTimeout(function(){
        _gv.$data.name = "大拽哥";
        _gv.$data.mum.name = "大拽姐";
        _gv.$data.mum.age = 34;
        _gv.$data.children.push({
            name:"狗娃",
            age:45
        });
        _gv.$data.children[0].name="gagaprince";
    },4000);

> html示例

    <div id="test">
        <div class="stdmsg">
            <div id="name" class="name">姓名:{{name}}</div>
            <div id="sex" class="sex">性别:{{sex}}</div>
            <div g-if="mum.age>30 || mum.age<20">
                <div id="mumName" class="mum-name" g-on:click="clickMe(3)">妈妈名字:{{mum.name}}</div>
                <div id="mumSex" class="mum-sex">妈妈性别:{{mum.sex}}</div>
            </div>
            <input type="text" g-model="mum.name"/>
            <!--<img g-bind:src="imgLink" alt="" />-->
            <div g-for="child in children" class="child">
                <div g-if="child.age>30" g-on:click="clickMe">
                孩子的名字 {{child.name}}
                </div>
            </div>

            <input type="text" g-model="mum.name"/>
        </div>
    </div>