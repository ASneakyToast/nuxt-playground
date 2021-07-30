<template>
  <div id="app">
    <Canvas
      width="full" height="full"
      :setup="setup" :loop="loop" />
  </div>
</template>

<script>
import Canvas from '@/components/Canvas'

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

class shapeItem {
  constructor( shape, position, velocity ) {
    this.shape = shape;
    this.width = shape.width;
    this.height = shape.height;
    this.x = position.x;
    this.y = position.y;
    this.vx = velocity.x;
    this.vy = velocity.y;
  }

  draw() {
    this.x = this.x + this.vx;
    this.y = this.y + this.vy;
    p5.ellipse(this.x, this.y, this.width, this.height);
  }
}

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

let shape = new shapeItem(
  {shape:'rect', width: 20, height: 20 },
  { x: 100, y: 100 },
  { vx: 0, y: 0 }
);
*/

export default {
  name: 'p5Test',
  components: {
    Canvas
  },
  data: () => {
    return {
      shape: {
        type: 'rect',
        x: 100, y: 100,
      },
    }
  },
  methods: {
    setup: (p5) => {

    },
    loop: (p5) => {
      p5.background('rgba(200,200,200,0.2)');
      p5.rect(20, 20, 20, 20);
      p5.rect(this.shape.x, this.shape.y, 20, 20);
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
