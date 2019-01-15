<template>
    <div class='sb_wrapper' v-bind:class='{ sb_wrapper_off: button_off }' :style="{'width': sb_wrapper_width + 'px', 'height': sb_wrapper_height + 'px', 'borderRadius': sb_wrapper_border_radius + 'px'}" @click='toggle()'>
        <transition name="fade-on">
            <span v-if='button_on' class='sb_button sb_button_on' :style="{'width': sb_button_size + 'px', 'height': sb_button_size + 'px', 'borderRadius': sb_button_border_radius + 'px'}"></span>
        </transition>
        <transition name="fade-off">
                <span v-if='button_off' class='sb_button sb_button_off' :style="{'width': sb_button_size + 'px', 'height': sb_button_size + 'px', 'borderRadius': sb_button_border_radius + 'px'}"></span>
        </transition>
    </div>
</template>


<script>
export default({
    name:'switch-button',
    // 父元素传入的数据
    props: {
        wrapper_width:{
            type:Number,
            default:200,
        },
        initial_state:{
            type: Boolean,
            default: false
        }
    },
    data(){
        return {
            sb_wrapper_width: this.wrapper_width,
            sb_wrapper_height: this.wrapper_width / 2,
            sb_wrapper_border_radius: this.wrapper_width / 4,
            sb_button_size: this.wrapper_width / 2 - 8,
            sb_button_border_radius: (this.wrapper_width / 2 - 8) / 2,
            button_on: this.initial_state,
            button_off: !this.initial_state
        }
    },
    mounted(){},
    methods:{
        toggle(){
            this.button_on = !this.button_on;
            this.button_off = !this.button_off;
            this.$emit("toggleBtn", this.button_on);
        }
    }
})
</script>


<style>
/* 
    sb_button_wrapper长宽比为9:5【变量】
    sb_button_wrapper的border-radius为宽的一半【变量】
    sb_button_wrapper的boder宽度为2px
 */
.sb_wrapper{
    display: inline-block;
    position: relative;
    border: 2px solid #ddd;
    box-sizing: border-box;
    background: #32CD32;
}
.sb_wrapper_off{
    background: #fff;
}
/* 
    sb_button长宽为sb_button_wrapper宽度减去8px【变量】
    sb_button的border-radius为长宽一半【变量】
    sb_button的boder宽度为2px
    sb_button的left或者right为2px【变量】
 */
.sb_button{
    display: inline-block;
    position: absolute;
    top: 2px;
    background: #fff;
    border: 2px solid #ddd;
    box-sizing: border-box;
}

.sb_button_on{
    right: 2px;
}

.sb_button_off{
    left: 2px;
}


/* 开始过渡阶段,动画出去阶段 */
.fade-on-enter-active{
    opacity: 1;
    transition: all 0.3s ease-out;
}
/* 进入开始 */
.fade-on-enter{
    transform: translateX(-100%);
    opacity: 1;
}

/* 开始过渡阶段,动画出去阶段 */
.fade-off-enter-active{
    opacity: 1;
    transition: all 0.3s ease-out;
}
/* 进入开始 */
.fade-off-enter{
    transform: translateX(100%);
    opacity: 1;
}
</style>
