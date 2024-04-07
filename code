let cols, rows;
let scl = 20;
let w = 1400;
let h = 1000;

let flying = 0;

let terrain = [];

function setup() {
  createCanvas(600, 600, WEBGL);
  cols = w / scl;
  rows = h / scl;

  for (let x = 0; x < cols; x++) {
    terrain[x] = [];
    for (let y = 0; y < rows; y++) {
      terrain[x][y] = 0; // 기본 값 설정
    }
  }
  // noStroke();
}

function draw() {

  flying -= 0.1;
  let yoff = flying;
  for (let y = 0; y < rows; y++) {
    var xoff = 0;
    for (let x = 0; x < cols; x++) {
      terrain[x][y] = map(noise(xoff, yoff), 0, 1, -100, 100);
      xoff += 0.2;
    }
    yoff += 0.2;
  }
  background(0, 128, 255);
  rotateX(PI / 3);
  // 변경된 지형 색상 설정
  fill(46, 139, 87);
  translate(-w / 2, -h / 2);
  for (var y = 0; y < rows - 1; y++) {
    beginShape(TRIANGLE_STRIP);
    for (var x = 0; x < cols; x++) {
      vertex(x * scl, y * scl, terrain[x][y]);
      vertex(x * scl, (y + 1) * scl, terrain[x][y + 1]);
    }
    endShape();
  }
  push(); 
  translate(w / 2, h / 2);
  translate(mouseX - width / 2, (mouseY - height / 2) * 6);
  rotate(PI / 5);
  // 수정된 비행기 모양
  fill(255, 0, 0); // 비행기 색상
  beginShape();
  vertex(0, 0, 0);
  vertex(30, -10, 0);
  vertex(20, 0, 0);
  vertex(30, 10, 0);
  endShape(CLOSE);
  pop();
}
