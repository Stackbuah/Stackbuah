let balas = [];
let inimigos = [];
let pontos = 0;
function setup() {
  createCanvas(400, 400);
  // Cria inimigos de acordo com o laço FOR:  
  for(let n = 0; n < 10; n++){
    criaInimigo();
  }
}
function draw() {
  background(240);
  verificaAcerto();
 
  // Percorre o array de inimigos
  for(let i of inimigos){
    // Finaliza o jogo se o inimigo chegar na parte de baixo da tela
    if(i.y > height-50){
      textAlign(CENTER);
      textSize(16);
      text("Você perdeu! Pontos: " + pontos, width/2,height-10);
      noLoop();
    }
    // movimenta o inimigo e desenha na tela
    i.y = i.y + 3;
    rect(i.x, i.y, i.t, i.t);  
  }
 
  // Percorre o array de balas
  for(let b of balas){
    // Verifica se chegou ao fim da tela para limpar memória
    if (b.y < 0){
      balas.splice(balas.indexOf(b), 1);
    }
   
    // Movimenta a bala e desenha na tela
    b.y = b.y - 5;
    circle(b.x, b.y, b.t);
  }
  // Desenha na tela o personagem
  circle(mouseX, height-50, 60)
}
function mousePressed(){
  // Cria o objeto "bala" na memória
  let bala = {
    x: mouseX,
    y: height-80,
    t: 8
  }
  balas.push(bala);
}
function criaInimigo(){
  // Cria um inimigo na memória
  let inimigo = {
    x: random(0, width-50),
    y: random(-800, 0),
    t: 30,
    i: int(random(0,2))
  }
  inimigos.push(inimigo);
}


function verificaAcerto(){
  for (let b of balas){
    for (let i of inimigos){
      let acertou = collideRectCircle(i.x, i.y, i.t, i.t, b.x, b.y, b.t);
      if (acertou == true){
        // remove o inimigo e a bala usando .splice
        inimigos.splice(inimigos.indexOf(i), 1);
        balas.splice(balas.indexOf(b), 1);
        criaInimigo();
        pontos++;
      }
    }
  }
}- 👋 Hi, I’m @Stackbuah
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Stackbuah/Stackbuah is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
