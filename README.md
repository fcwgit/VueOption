# VueOption
自定义标签
<header>

    </header>

定义扩展
var header_a = Vue.extend({
            template:`<p>{{message}}</p>`,
            data:function(){
                return {
                    message:'Hello ,I am header'
                }
            }
        });

绑定
new header_a().$mount('header');

注意：绑定标签直接使用'标签名'接口，绑定id则使用'#id'

接收传值
template:`<p>{{message}}  --  {{a}}</p>`,
            data:function(){
                return {
                    message:'Hello ,I am header'
                }
            },
            props:['a']
        });

        new header_a({propsData:{a:1}}).$mount('header');


==========================================
var vm = new Vue({
            el:'#app',
            data:{
                message:'test',
                price:10
            },
            computed:{
                newPrice:function(){
                    return '￥' + this.price + '元';
                }
            }
        })

在不污染原始数据的情况下，对选项值进行改造
var newList = [
            {title:'aaaa',date:'2017/3/24'},
            {title:'bbbb',date:'2017/5/24'},
            {title:'cccc',date:'2017/3/21'},
            {title:'dddd',date:'2017/5/27'}
        ]
reverNews:function(){
                    return this.newList.reverse();
                }
===================methods=======================
<p>{{num}}</p>
        <p><button @click="add">add</button></p>

var vm = new Vue({
            el:'#app',
            data:{
                num:1
            },
            methods:{
                add:function(){
                    this.num++;
                }
            }
        })

传值
<p><button @click="add(2)">add</button></p>
methods:{
                add:function(a){
                    if(a != ''){
                        this.num += a;
                    }else{
                        this.num++;
                    }
                    
                }
            }
传递点击事件对象，实现交互性比较高的场景
add:function(a,event){
                    if(a != ''){
                        this.num += a;
                    }else{
                        this.num++;
                    }
                    console.log(event);
                }


自定义组件，使用native调用标签方法
<p><btn @click.native="add(5)"></btn></p>
var btn={
            template:`<button>组件btn——add</button>`
        }
components:{
                'btn':btn
            },

作用域外面使用原始的onclick方法调用构造器内方法
<button onclick="vm.add(7)">add</button>


===================watch    =======================
<p>今日温度：{{num}}</p>
        <p><button @click="shenggao">升高</button></p>
        <p><button @click="jiangdi">降低</button></p>
        <p>穿衣建议：{{chuanyi}}</p>

watch监控num的变化
data:{
                message:'test',
                num:1,
                chuanyi:'夹克长裙'
            },
            methods:{
                shenggao:function(){
                    this.num+=5;
                },
                jiangdi:function(){
                    this.num-=5;
                }   
            },
            watch:{
                  num:function(newVal,oldVal){
                      if(newVal >= 26){
                          this.chuanyi = 'T恤短袖';
                      }else if(newVal <26 && newVal>=0 ){
                          this.chuanyi = '夹克长裙'
                      }else{
                          this.chuanyi = '棉衣羽绒服';
                      }
                  }
            }

也可以在构造器外面进行监听
vm.$watch('num',function(newVal,oldVal){
            if(newVal >= 26){
                this.chuanyi = 'T恤短袖';
            }else if(newVal <26 && newVal>=0 ){
                this.chuanyi = '夹克长裙'
            }else{
                this.chuanyi = '棉衣羽绒服';
            }
        });









