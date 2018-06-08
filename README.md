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

