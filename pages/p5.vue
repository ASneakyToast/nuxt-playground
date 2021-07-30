<template>
  <div id="app">
    <div id="Canvas" ref="Canvas"></div>
  </div>
</template>

<script>
/*
const eater = ( state ) => ({
  eat( amount ) {
    console.log(`${ state.name } is eating.`);
    state.energy += amount
  }
});

function Dog ( name, energy, breed ) {
  let dog = {
    name,
    energy,
    breed,
  }

  return Object.assign(
    dog,
    eater( dog ),
  )
}

const leo = Dog('Leo', 10, 'Goldendoogle');
let.eat(10);
*/

/*
const mover = ( state ) => ({
  move( amount ) {
    state.pos.x += amount.x;
    state.pos.y += amount.y;
  }
})

function Rect ( pos, size ) {
  let rect = {
    pos,
    size,
  }

  function draw() {
    p5.rect( rec.pos.x, rect.pos.y, rect.size.x, rect.size.y );
  }

  return Object.assign(
    rect,
    draw(),
    mover( rect ),
  )
}

*/

/*
class Emitter {
  constructor( position ) {
    this.x = position.x;
    this.y = position.y;
    this.items = [];
  }

  setItem( item ) {
    this.item = item;
  }

  draw() {
    for ( item in items ) {
      item.draw();
    }
  }
}

*/
class Agent {
  constructor( shape, position, velocity ) {
    this.shape = shape;
    this.width = shape.width;
    this.height = shape.height;
    this.x = position.x;
    this.y = position.y;
    this.vx = velocity.x;
    this.vy = velocity.y;
  }

  draw(p5) {
    this.x = this.x + this.vx;
    this.y = this.y + this.vy;
    p5.ellipse(this.x, this.y, this.width, this.height);
  }
}

/*
let shape = new Agent(
  {shape:'rect', width: 20, height: 20 },
  { x: 300, y: 300 },
  { vx: 0, y: 0 }
);
*/

export default {
  name: 'p5Test',
  data: () => {
    return {
      width: "full",
      height: "full",
    }
  },
  mounted() {
    const script = p5 => {
      let shape = new Agent(
        {shape:'rect', width: 20, height: 20 },
        { x: 300, y: 300 },
        { vx: 0, y: 0 }
      );

      p5.setup = () => {
        let canvas;
        if ( this.width == "full" && this.height == "full" ) {
          this.$nextTick(function() {
            let element = this.$refs["Canvas"];
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
        shape.draw(p5);
      };
    }
    const P5 = require('p5');
    new P5(script);
  },
  methods: {
    setup: (p5) => {

    },
    loop: (p5) => {
      p5.background('rgba(200,200,200,0.2)');
      p5.rect(20, 20, 20, 20);
      p5.ellipse(p5.mouseX, p5.mouseY, 40, 40);
    },
  }
}
</script>

<style>
  html, body {
    height: 100%;
    width: 100%
  } 
  
  body, canvas {
    margin: 0;
    padding: 0;
  }


  #app, #__nuxt, #__layout {
    height: 100%;
  }

  #Canvas {
    width: 100%;
    height: 100%;
  }
</style>
