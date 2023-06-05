let bullets = []
let enemies = []
let score = 0

function setup() {
  createCanvas(400, 400);
  for(let i = 0;i<10;i++){
    let enemy = {
      x: random(0,width),
      y: random(-800, 0)
    }
    enemies.push(enemy)
  }
}

function draw() {
  background(51);
  rectMode(CENTER)
  circle(mouseX, height - 50 ,25)
  for(let bullet of bullets){
    bullet.y -= 10
    circle(bullet.x,bullet.y,10)
  }
  for(let enemy of enemies){
    enemy.y +=2
    rect(enemy.x , enemy.y , 10)
    if(enemy.y > height){
      text("Game Over!" ,width/2,height/2)
      noLoop()
    }
  }
  for(let enemy of enemies){
    for(let bullet of bullets){
      if(dist(enemy.x, enemy.y,bullet.x,bullet.y) < 10 ){
        enemies.splice(enemies.indexOf(enemy) , 1)
        bullets.splice(bullets.indexOf(bullet) ,1)
    let NewEnemy = {
        x: random(0,width),
        y: random(-800, 0)
    }
    enemies.push(NewEnemy)
    score+=1
  }
      }
    }
  text(score,15,25)
}
function mousePressed(){
  let bullet = {
    x: mouseX,
    y: height - 50 
  }
  bullets.push(bullet)
}
