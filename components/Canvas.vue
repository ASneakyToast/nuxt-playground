<template>
  <div id="Canvas" ref="Canvas"></div>
</template>

<script>
export default {
  name: 'App',
  props: {
    width: [ Number, String ],
    height: [ Number, String ],
    setup: Function,
    loop: Function,
  },
  mounted() {
    const script = p5 => {
      p5.setup = () => {
        let canvas;
        if ( this.width == "full" && this.height == "full" ) {
          this.$nextTick(function() {
            let element = this.$refs["Canvas"];
            console.log(element);
            canvas = p5.createCanvas( element.offsetWidth, element.offsetHeight );
            canvas.parent("Canvas");
          })
        } else {
          canvas = p5.createCanvas(this.width, this.height);
          canvas.parent("Canvas");
        }
        this.setup(p5);
      };
      p5.draw = () => {
        this.loop(p5);
      };
    }
    const P5 = require('p5');
    new P5(script);
  },
}
</script>

