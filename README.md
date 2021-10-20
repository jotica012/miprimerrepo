# miprimerrepo
 Ejercicio 1: 1 codigo visual estudio que ocnstruya por lo menos 1 obj en JS 
class Circulo{
  constructor(x, y){
    this.x = x;
    this.y = y;
    this.tam  = 50;

  }
  pintar(){
    noStroke();
    fill(255,240,0);
    circle(this.x, this.y, this.tam);
  }
}

class Triangulo{
  constructor(x, y,){
    this.x = x;
    this.y = y;
  }
  pintar(){
    fill(255,0,0);
    triangle(this.x-25, this.y+25, this.x+25, this.y+25, this.x, this.y-25);
  }
}

class Rombo{
  constructor(x, y){
    this.x = x;
    this.y = y;
  }
  pintar(){
    fill(0,230,0);
    quad(this.x-25, this.y, this.x, this.y+25, this.x+25, this.y, this.x, this.y-25);
  }
}

class Cuadrado{
  constructor(x, y){
    this.x = x;
    this.y = y;
  }
  pintar(){
    fill(0,0,255);
    rectMode(CENTER);
    rect(this.x, this.y, 50, 50);
    rectMode(CORNER);
  }
}

class Zonas{
  constructor(x, y, trazo = [0,0,0]){
    this.x = x;
    this.y = y;
    this.trazo = trazo;

  }
  pintar(){
    stroke(this.trazo);
    strokeWeight(4);
    fill(255);
    rect(this.x,this.y,150,120);
  }
}

let circulo;
let triangulo;
let rombo;
let cuadrado;

let zona1;
let zona2;
let zona3;
let zona4;

let isGreen = [0,255,0];
let isRed = [255,0,0];

function setup() {
  createCanvas(400, 400);
  circulo = new Circulo(80,350,50);
  triangulo = new Triangulo(150,350);
  rombo = new Rombo(220,350);
  cuadrado = new Cuadrado(300,350);

  zona1 = new Zonas(50,50,0);
  zona2 = new Zonas(200,50,0);
  zona3 = new Zonas(50,170,0);
  zona4 = new Zonas(200,170,0);
}

function draw() {
  background(220);

  zona1.pintar();
  zona2.pintar();
  zona3.pintar();
  zona4.pintar();

  //Circulo
  fill(255);
  stroke(255,240,0)
  circle(125, 110, 60);

  //Triángulo
  stroke(255,0,0);
  triangle(270-25, 110+25, 270+25, 110+25, 270, 110-25);

  //rombo
  stroke(0,230,0);
  quad(125-30, 230, 125, 230+30, 125+30, 230, 125, 230-30);

  //cuadrado
  stroke(0,0,255);
  rect(250,210, 50,50);

  circulo.pintar();
  triangulo.pintar();
  rombo.pintar();
  cuadrado.pintar();

  if(circulo.x > zona1.x && circulo.x < zona1.x + 150
    && circulo.y > zona1.y && circulo.y < zona1.y + 120){
      zona1.trazo = isGreen;
    }else if(triangulo.x > zona1.x && triangulo.x < zona1.x + 150
      && triangulo.y > zona1.y && triangulo.y < zona1.y + 120
      ||rombo.x > zona1.x && rombo.x < zona1.x + 150
      && rombo.y > zona1.y && rombo.y < zona1.y + 120
      ||cuadrado.x > zona1.x && cuadrado.x < zona1.x + 150
      && cuadrado.y > zona1.y && cuadrado.y < zona1.y + 120){
        zona1.trazo = isRed;
    } else{
        zona1.trazo = [0,0,0];
    }

    if(triangulo.x > zona2.x && triangulo.x < zona2.x + 150
      && triangulo.y > zona2.y && triangulo.y < zona2.y + 120){
        zona2.trazo = isGreen;
      }else if(circulo.x > zona2.x && circulo.x < zona2.x + 150
        && circulo.y > zona2.y && circulo.y < zona2.y + 120
        ||rombo.x > zona2.x && rombo.x < zona2.x + 150
        && rombo.y > zona2.y && rombo.y < zona2.y + 120
        ||cuadrado.x > zona2.x && cuadrado.x < zona2.x + 150
        && cuadrado.y > zona2.y && cuadrado.y < zona2.y + 120){
          zona2.trazo = isRed;
      } else{
          zona2.trazo = [0,0,0];
      }

    if(rombo.x > zona3.x && rombo.x < zona3.x + 150
      && rombo.y > zona3.y && rombo.y < zona3.y + 120){
        zona3.trazo = isGreen;
      }else if(circulo.x > zona3.x && circulo.x < zona3.x + 150
        && circulo.y > zona3.y && circulo.y < zona3.y + 120
        ||triangulo.x > zona3.x && triangulo.x < zona3.x + 150
        && triangulo.y > zona3.y && triangulo.y < zona3.y + 120
        ||cuadrado.x > zona3.x && cuadrado.x < zona3.x + 150
        && cuadrado.y > zona3.y && cuadrado.y < zona3.y + 120){
          zona3.trazo = isRed;
      } else{
          zona3.trazo = [0,0,0];
      }
    
  if(cuadrado.x > zona4.x && cuadrado.x < zona4.x + 150
    && cuadrado.y > zona4.y && cuadrado.y < zona4.y + 120){
        zona4.trazo = isGreen;
      }else if(circulo.x > zona4.x && circulo.x < zona4.x + 150
        && circulo.y > zona4.y && circulo.y < zona4.y + 120
        ||rombo.x > zona4.x && rombo.x < zona4.x + 150
        && rombo.y > zona4.y && rombo.y < zona4.y + 120
        ||triangulo.x > zona4.x && triangulo.x < zona4.x + 150
        && triangulo.y > zona4.y && triangulo.y < zona4.y + 120){
          zona4.trazo = isRed;
      } else{
          zona4.trazo = [0,0,0];
      }
}
  

function mouseDragged(){
  if(dist(mouseX, mouseY, circulo.x, circulo.y)<25){
    circulo.x = mouseX;
    circulo.y = mouseY;
  }

  if(dist(mouseX, mouseY, triangulo.x, triangulo.y)<25){
    triangulo.x = mouseX;
    triangulo.y = mouseY;
  }

  if(dist(mouseX, mouseY, rombo.x, rombo.y)<25){
    rombo.x = mouseX;
    rombo.y = mouseY;
  }

  if(dist(mouseX, mouseY, cuadrado.x, cuadrado.y)<25){
    cuadrado.x = mouseX;
    cuadrado.y = mouseY;
  }
}
