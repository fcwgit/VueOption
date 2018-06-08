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





