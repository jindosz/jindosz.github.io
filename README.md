# jindosz.github.io

code :
let xpos, ypos;
let vx, vy;
let ax, ay;
let dt;
let onSpectrum;

function setup() {
  createCanvas(windowWidth, windowHeight);
  
  onSpectrum = createCheckbox('잔상 남기기');
  onSpectrum.position(0, 0);
  
  xpos = 10; //왼 -> 오 +
  ypos = windowHeight-10; // 위 -> 아 +
  
  vx = 10;
  vy = 7;
  
  ay = 2; //y개민감
  ax = 0;
  dt = 0.1;
  
  if (onSpectrum.checked()) {
    background('grey');
  }
  
  print(windowHeight);
  print(windowWidth);
}

function draw() {
  if (onSpectrum.checked() == false) {
      background('grey');
      }
  
  if (ypos > windowHeight || ypos < 0) {
    vy *= -1;
    vy /= 1.0;
  } // y축 반동
  
  if (xpos > windowWidth || xpos < 0) {
    vx *= -1;
    ax *= -1;
  } // x축 반동
  
  xpos += vx*dt;
  ypos -= vy+dt;
  
  vy -= ay*dt;
  vx += ax*dt;
  
  circle(xpos, ypos, 10)
}
