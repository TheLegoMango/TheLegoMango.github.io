# TheLegoMango.github.io
<html> 
  <head>
    <title> WIRES!</title> 
    <style>
        body{
            background-color:rgb(0,0,0);
        }
        h1{
            color:rgb(255,0,0);
        }
    </style>
  </head>
  <body>
    <br>
    ..............................................................................<h1>Wires!<br>by TheLegoMango<br>on Khan Academy</h1>
    <br>
    <br>............................................................................................................................
	<!--This draws the canvas on the webpage -->
    <canvas id="mycanvas"></canvas> 
  </body>
 
  <!-- Include the processing.js library -->
  <!-- See https://khanacademy.zendesk.com/hc/en-us/articles/202260404-What-parts-of-ProcessingJS-does-Khan-Academy-support- for differences -->
  <script src="https://cdn.jsdelivr.net/processing.js/1.4.8/processing.min.js"></script> 
  <script>
  var programCode = function(processingInstance) {
    with (processingInstance) {
      size(500, 600); 
      frameRate(60);
 





//levels
var levels=[
    {
        lev:[
            "      ",
            "      ",
            "  @/  ",
            "      ",
            "      ",
            "      ",
        ],
        loc:[
            'TTTTTT',
            'TTTTTT',
            'TTTTTT',
            'TTTTTT',
            'TTTTTT',
            'TTTTTT',
        ],
        res:{
            '@':0,
            '/':0,
            '|':0,
            'L':0,
            'T':0,
            '+':0,
            "'":0,
        }
    },
    {
        lev:[
            "      ",
            "      ",
            "  @|/ ",
            "      ",
            "      ",
            "      ",
        ],
        loc:[
            'TTTTTT',
            'TTTTTT',
            'TTTTTT',
            'TTTTTT',
            'TTTTTT',
            'TTTTTT',
        ],
        res:{
            '@':0,
            '/':0,
            '|':0,
            'L':0,
            'T':0,
            '+':0,
            "'":0,
        }
    },
    {
        lev:[
            "      ",
            "      ",
            "  @L/ ",
            "  LL  ",
            "      ",
            "      ",
        ],
        loc:[
            'TTTTTT',
            'TTTTTT',
            'TTTTTT',
            'TTTTTT',
            'TTTTTT',
            'TTTTTT',
        ],
        res:{
            '@':0,
            '/':0,
            '|':0,
            'L':0,
            'T':0,
            '+':0,
            "'":0,
        }
    },
    {
        lev:[
            "      ",
            "      ",
            "  @T/ ",
            "   '  ",
            "      ",
            "      ",
        ],
        loc:[
            'TTTTTT',
            'TTTTTT',
            'TTTTTT',
            'TTTTTT',
            'TTTTTT',
            'TTTTTT',
        ],
        res:{
            '@':0,
            '/':0,
            '|':0,
            'L':0,
            'T':0,
            '+':0,
            "'":0,
        }
    },
    {
        lev:[
            "    TL ",
            "   L+L ",
            "  @+/  ",
            "   '   ",
            "       ",
            "       ",
        ],
        loc:[
            'TTTTTT',
            'TTTTTT',
            'TTTTTT',
            'TTTTTT',
            'TTTTTT',
            'TTTTTT',
        ],
        res:{
            '@':0,
            '/':0,
            '|':0,
            'L':0,
            'T':0,
            '+':0,
            "'":0,
        }
    },
    {
        lev:[
            "      ",
            "  @ / ",
            "      ",
            "      ",
        ],
        loc:[
            'TTTTTT',
            'TTTFTT',
            'TTTTTT',
            'TTTTTT',
        ],
        res:{
            '@':0,
            '/':0,
            '|':1,
            'L':0,
            'T':0,
            '+':0,
            "'":0,
        }
    },
    {
        lev:[
            "      ",
            "   +  ",
            "  @/  ",
            "      ",
            "      ",
        ],
        loc:[
            'TTTFTT',
            'TTFTFT',
            'TTTTTT',
            'TTTTTT',
            'TTTTTT',
        ],
        res:{
            '@':0,
            '/':0,
            '|':0,
            'L':0,
            'T':0,
            '+':0,
            "'":3,
        }
    },
    {
        lev:[
            "       ",
            "   LL  ",
            "  @T+' ",
            "   | ' ",
            " '+''  ",
            "       ",
        ],
        loc:[
            'TTTTTT ',
            'TTTTTT ',
            'TTTFTT ',
            'TTFTFT ',
            'TTTTTT ',
            'FFFFFF ',
        ],
        res:{
            '@':0,
            '/':1,
            '|':0,
            'L':1,
            'T':0,
            '+':1,
            "'":0,
        }
    },
    {
        lev:[
            "  + L",
            "++TLL",
        ],
        loc:[
            'FFTF',
            'TTTT',
        ],
        res:{
            '@':1,
            '/':1,
            '|':0,
            'L':0,
            'T':0,
            '+':0,
            "'":1,
        }
    },
    {
        lev:[
            "       ",
            "       ",
            "  @    ",
            "       ",
            "       ",
            "     / ",
            "       ",
        ],
        loc:[
            'FFFFFFF',
            'FFFFFFF',
            'FFFFFFF',
            'FFFFFFF',
            'FFFFTTF',
            'FFFFTFF',
            'FFFFFFF',
        ],
        res:{
            '@':0,
            '/':0,
            '|':2,
            'L':2,
            'T':2,
            '+':2,
            "'":2,
        }
    },
    {
        lev:[
            "L||++",
            "++@/+",
            "L||++",
        ],
        loc:[
            'TTTTTT',
            'TTTTTT',
            'TTTTTT',
        ],
        res:{
            '@':0,
            '/':0,
            '|':0,
            'L':0,
            'T':0,
            '+':0,
            "'":0,
        }
    },
    {
        lev:[""],
        loc:[""],
        res:{}
    }
];



//da code{

background(0);

/* jshint ignore:start */

var pointer=[
    "b",
    "bb",
    "bwb",
    "bwwb",
    "bwwwb",
    "bwwwwb",
    "bwwwwwb",
    "bwwwwwbb",
    "bwbwwb",
    "bb bwwb",
    "   bwwb",
    "    bwwb",
    "     bb",
];

function clickHere(x,y){
    pushMatrix();
    translate(x,y);
    scale(3+sin(frameCount/50)/2);
    for(var i=0;i<pointer.length;i++){
        for(var j=0;j<pointer[i].length;j++){
            switch(pointer[i][j]){
                case 'b':
                    fill(0,100);
                break;
                case 'w':
                    fill(255,100);
                break;
                case ' ':
                    noFill();
                break;
            }
            noStroke();
            rect(j,i,1,1);
        }
    }
    popMatrix();
}

var sel=0;
var inPlay;

var win='q';

var Level=0;

var cLevels=[];

function piece(x,y,w,h,type,loc){
    this.x=x;
    this.y=y;
    this.w=w;
    this.h=h;
    this.type=type;
    this.loc=loc;
    this.r=0;
    this.on=0;
}

function confetti(){
    this.pieces=[];
}
confetti.prototype.all=function(){
    if(frameCount%random(100,200)<2){
        this.pieces.push(new piece(
            random(0,width),
            -50,
            random(50,80),
            random(50,80),
            "@/|LT+'"[floor(random(6))],
            random()<0.5?"T":"F"
        ));
    }
    for(var i=0;i<this.pieces.length;i++){
        this.pieces[i].all([""],0,0);
        this.pieces[i].y+=noise(this.pieces[i].x,this.pieces[i].y)*4;
        this.pieces[i].x+=sin(frameCount/5)/20;
        this.pieces[i].r+=10+sin(frameCount/50+i*10)*9;
    }
};

var rain=new confetti();

function level(numX,numY,lev){
    this.pieces=[];
    for(var i=0;i<500;i+=ceil(500/numX)){
        this.pieces.push([]);
        for(var j=0;j<500;j+=ceil(500/numY)){
            this.pieces[round(i/500*numX)].push(new piece(
                i, j,
                500/numX, 500/numY,
                lev.lev [round(j/500*numY)][round(i/500*numX)],
                lev.loc [round(j/500*numY)][round(i/500*numX)]
            ));
        }
    }
    this.res={
        '@':lev.res['@'],
        '/':lev.res['/'],
        '|':lev.res['|'],
        'L':lev.res['L'],
        'T':lev.res['T'],
        '+':lev.res['+'],
        "'":lev.res["'"],
    };
}

level.prototype.all=function(){
    for(var i=0;i<this.pieces.length;i++){
        for(var j=0;j<this.pieces[i].length;j++){
            this.pieces[i][j].all(this.pieces,i,j);
        }
    }
    fill(255);
    stroke(0);
    strokeWeight(4);
    rect(0,500,500,100);
    for(var i=500/14;i<500;i+=500/7){
        switch(round(i/500*7-0.5)){
            case 0:
                fill(255, 0, 0);
                textSize(20);
                text(this.res['@'],i,520);
                fill(0,10);
                noStroke();
                for(var j=50;j>10;j--){
                    ellipse(i,560,j,j);
                }
                
            break;
            case 1:
                fill(255, 0, 0);
                textSize(20);
                text(this.res['/'],i,520);
                fill(255, 200, 0);
                stroke(0);
                strokeWeight(2);
                rectMode(CENTER);
                rect(i,560,25,50);
                rect(i,577,17,35);
                fill(0);
                textSize(10);
                textAlign(CENTER,CENTER);
                text("OFF",i,550);
                
            break;
            case 2:
                fill(255, 0, 0);
                textSize(20);
                text(this.res['|'],i,520);
                stroke(0);
                strokeWeight(10);
                line(i,540,i,590);
            break;
            case 3:
                fill(255, 0, 0);
                textSize(20);
                text(this.res['L'],i,520);
                stroke(0);
                strokeWeight(10);
                line(i,540,i,564);
                line(i,565,i+25,565);
                
            break;
            case 4:
                fill(255, 0, 0);
                textSize(20);
                text(this.res['T'],i,520);
                stroke(0);
                strokeWeight(10);
                line(i,565,i,590);
                line(i-25,565,i+25,565);
                
            break;
            case 5:
                fill(255, 0, 0);
                textSize(20);
                text(this.res['+'],i,520);
                stroke(0);
                strokeWeight(10);
                line(i,540,i,590);
                line(i-25,565,i+25,565);
                
            break;
            case 6:
                fill(255, 0, 0);
                textSize(20);
                text(this.res["'"],i,520);
                stroke(0);
                strokeWeight(10);
                line(i,540,i,565);
                
            break;
        }
        if(round(i/500*7-0.5)===sel){
            noFill();
            stroke(0);
            strokeWeight(3);
            rectMode(CENTER);
            rect(i,550,60,90);
        }
    }
};

function lose(){
    cLevels[Level]=new level(
        levels[Level].lev[0].length,
        levels[Level].lev.length,
        levels[Level]
    );
    win='q';
}

//pieces prototypes{

piece.prototype.click=function(){
    switch(this.type){
        case '@':
            
        break;
        case '/':
            this.type='\\';
        break;
        case '\\':
            this.type='/';
        break;
        case '|':
            this.r+=90;
            this.r=this.r%360;
        break;
        case 'L':
            this.r+=90;
            this.r=this.r%360;
        break;
        case 'T':
            this.r+=90;
            this.r=this.r%360;
        break;
        case '+':
            this.r+=90;
            this.r=this.r%360;
        break;
        case "'":
            this.r+=90;
            this.r=this.r%360;
        break;
        case ' ':
            if(this.loc==='F'){
                switch(sel){
                    case 0:
                        if(cLevels[Level].res['@']>0){
                            cLevels[Level].res[this.type]++;
                            this.type='@';
                            cLevels[Level].res['@']--;
                        }
                    break;
                    case 1:
                        if(cLevels[Level].res['/']>0){
                            cLevels[Level].res[this.type]++;
                            this.type='/';
                            cLevels[Level].res['/']--;
                        }
                    break;
                    case 2:
                        if(cLevels[Level].res['|']>0){
                            cLevels[Level].res[this.type]++;
                            this.type='|';
                            cLevels[Level].res['|']--;
                        }
                    break;
                    case 3:
                        if(cLevels[Level].res['L']>0){
                            cLevels[Level].res[this.type]++;
                            this.type='L';
                            cLevels[Level].res['L']--;
                        }
                    break;
                    case 4:
                        if(cLevels[Level].res['T']>0){
                            cLevels[Level].res[this.type]++;
                            this.type='T';
                            cLevels[Level].res['T']--;
                        }
                    break;
                    case 5:
                        if(cLevels[Level].res['+']>0){
                            cLevels[Level].res[this.type]++;
                            this.type='+';
                            cLevels[Level].res['+']--;
                        }
                    break;
                    case 6:
                        if(cLevels[Level].res["'"]>0){
                            cLevels[Level].res[this.type]++;
                            this.type="'";
                            cLevels[Level].res["'"]--;
                        }
                    break;
                }
            }
        break;
    }
};

piece.prototype.left=function(ar,I,J){
    if(ar[I-1]&&this.on){switch(ar[I-1][J].type){
                case '@':
                    ar[I-1][J].on=1;
                break;
                case '|':
                    if(ar[I-1][J].r===90||ar[I-1][J].r===270){
                        ar[I-1][J].on=1;
                    }
                    else{
                        lose();
                    }
                break;
                case 'L':
                    if(ar[I-1][J].r===0||ar[I-1][J].r===90){
                        ar[I-1][J].on=1;
                    }
                    else{
                        lose();
                    }
                break;
                case 'T':
                    if(ar[I-1][J].r!==90){
                        ar[I-1][J].on=1;
                    }
                    else{
                        lose();
                    }
                break;
                case '+':
                    ar[I-1][J].on=1;
                break;
                case "'":
                    if(ar[I-1][J].r===90){
                        ar[I-1][J].on=1;
                    }
                    else{
                        lose();
                    }
                break;
                case ' ':
                    lose();
                break;
            }}
};

piece.prototype.right=function(ar,I,J){
    if(ar[I+1]&&this.on){switch(ar[I+1][J].type){
                case '@':
                    ar[I+1][J].on=1;
                break;
                case '|':
                    if(ar[I+1][J].r===90||ar[I+1][J].r===270){
                        ar[I+1][J].on=1;
                    }
                    else{
                        lose();
                    }
                break;
                case 'L':
                    if(ar[I+1][J].r===180||ar[I+1][J].r===270){
                        ar[I+1][J].on=1;
                    }
                    else{
                        lose();
                    }
                break;
                case 'T':
                    if(ar[I+1][J].r!==270){
                        ar[I+1][J].on=1;
                    }
                    else{
                        lose();
                    }
                break;
                case '+':
                    ar[I+1][J].on=1;
                break;
                case "'":
                    if(ar[I+1][J].r===270){
                        ar[I+1][J].on=1;
                    }
                    else{
                        lose();
                    }
                break;
                case ' ':
                    lose();
                break;
            }}
};

piece.prototype.down=function(ar,I,J){
    if(ar[I][J+1]&&this.on){switch(ar[I][J+1].type){
                case '@':
                    ar[I][J+1].on=1;
                break;
                case '|':
                    if(ar[I][J+1].r===0||ar[I][J+1].r===180){
                        ar[I][J+1].on=1;
                    }
                    else{
                        lose();
                    }
                break;
                case 'L':
                    if(ar[I][J+1].r===0||ar[I][J+1].r===270){
                        ar[I][J+1].on=1;
                    }
                    else{
                        lose();
                    }
                break;
                case 'T':
                    if(ar[I][J+1].r!==0){
                        ar[I][J+1].on=1;
                    }
                    else{
                        lose();
                    }
                break;
                case '+':
                    ar[I][J+1].on=1;
                break;
                case "'":
                    if(ar[I][J+1].r===0){
                        ar[I][J+1].on=1;
                    }
                    else{
                        lose();
                    }
                break;
                case ' ':
                    lose();
                break;
            }}
};

piece.prototype.up=function(ar,I,J){
    if(ar[I][J-1]&&this.on){switch(ar[I][J-1].type){
                case '@':
                    ar[I][J-1].on=1;
                break;
                case '|':
                    if(ar[I][J-1].r===0||ar[I][J-1].r===180){
                        ar[I][J-1].on=1;
                    }
                    else{
                        lose();
                    }
                break;
                case 'L':
                    if(ar[I][J-1].r===90||ar[I][J-1].r===180){
                        ar[I][J-1].on=1;
                    }
                    else{
                        lose();
                    }
                break;
                case 'T':
                    if(ar[I][J-1].r!==180){
                        ar[I][J-1].on=1;
                    }
                    else{
                        lose();
                    }
                break;
                case '+':
                    ar[I][J-1].on=1;
                break;
                case "'":
                    if(ar[I][J-1].r===180){
                        ar[I][J-1].on=1;
                    }
                    else{
                        lose();
                    }
                break;
                case ' ':
                    lose();
                break;
            }}
};

piece.prototype.all=function(ar,I,J){
    fill(255);
    stroke(0);
    strokeWeight(2);
    rectMode(CORNER);
    rect(this.x,this.y,this.w,this.h);
    pushMatrix();
    translate(this.x+this.w/2,this.y+this.h/2);
    fill(150);
    stroke(0);
    for(var i=0;i<4;i++){
        pushMatrix();
        rotate(i*PI/2);
        if(this.loc!=="F"){
            if(i%2){
                ellipse(this.h/2-5,this.w/2-5,5,5);
            }
            else{
                ellipse(this.w/2-5,this.h/2-5,5,5);
            }
        }
        popMatrix();
    }
    rotate(this.r/180*PI);
    switch(this.type){
        
        case '@':{
            fill(this.on*255, 0, 0, 10);
            noStroke();
            for(
                var i=(this.w<this.h?this.w:this.h);
                i>10;i--
            ){
                ellipse(0,0,i,i);
            }
            if(this.on){
                win=(win>0)?win:0;
            }
        }break;
        
        case '/':{
            
            stroke(0);
            strokeWeight(10);
            if(ar[I-1]){switch(ar[I-1][J].type){
                case '@':
                    line(0,0,-this.w/2,0);
                break;
                case '|':
                    if(ar[I-1][J].r===90||ar[I-1][J].r===270){
                        line(0,0,-this.w/2,0);
                    }
                break;
                case 'L':
                    if(ar[I-1][J].r===0||ar[I-1][J].r===90){
                        line(0,0,-this.w/2,0);
                    }
                break;
                case 'T':
                    if(ar[I-1][J].r!==90){
                        line(0,0,-this.w/2,0);
                    }
                break;
                case '+':
                    line(0,0,-this.w/2,0);
                break;
                case "'":
                    if(ar[I-1][J].r===90){
                        line(0,0,-this.w/2,0);
                    }
                break;
            }}
            if(ar[I+1]){switch(ar[I+1][J].type){
                case '@':
                    line(0,0,this.w/2,0);
                break;
                case '|':
                    if(ar[I+1][J].r===90||ar[I+1][J].r===270){
                        line(0,0,this.w/2,0);
                    }
                break;
                case 'L':
                    if(ar[I+1][J].r===180||ar[I+1][J].r===270){
                        line(0,0,this.w/2,0);
                    }
                break;
                case 'T':
                    if(ar[I+1][J].r!==270){
                        line(0,0,this.w/2,0);
                    }
                break;
                case '+':
                    line(0,0,this.w/2,0);
                break;
                case "'":
                    if(ar[I+1][J].r===270){
                        line(0,0,this.w/2,0);
                    }
                break;
            }}
            if(ar[I][J-1]){switch(ar[I][J-1].type){
                case '@':
                    line(0,0,0,-this.h/2);
                break;
                case '|':
                    if(ar[I][J-1].r===0||ar[I][J-1].r===180){
                        line(0,0,0,-this.h/2);
                    }
                break;
                case 'L':
                    if(ar[I][J-1].r===90||ar[I][J-1].r===180){
                        line(0,0,0,-this.h/2);
                    }
                break;
                case 'T':
                    if(ar[I][J-1].r!==180){
                        line(0,0,0,-this.h/2);
                    }
                break;
                case '+':
                    line(0,0,0,-this.h/2);
                break;
                case "'":
                    if(ar[I][J-1].r===180){
                        line(0,0,0,-this.h/2);
                    }
                break;
            }}
            if(ar[I][J+1]){switch(ar[I][J+1].type){
                case '@':
                    line(0,0,0,this.h/2);
                break;
                case '|':
                    if(ar[I][J+1].r===0||ar[I][J+1].r===180){
                        line(0,0,0,this.h/2);
                    }
                break;
                case 'L':
                    if(ar[I][J+1].r===0||ar[I][J+1].r===270){
                        line(0,0,0,this.h/2);
                    }
                break;
                case 'T':
                    if(ar[I][J+1].r!==0){
                        line(0,0,0,this.h/2);
                    }
                break;
                case '+':
                    line(0,0,0,this.h/2);
                break;
                case "'":
                    if(ar[I][J+1].r===0){
                        line(0,0,0,this.h/2);
                    }
                break;
            }}
            
            fill(255, 200, 0);
            stroke(0);
            strokeWeight(2);
            rectMode(CENTER);
            rect(0,0,this.w/4,this.h/2);
            rect(0,this.h/6,this.w/6,this.h/3);
            fill(0);
            textSize((this.w<this.h?this.w:this.h)/10);
            textAlign(CENTER,CENTER);
            text("OFF",0,-this.h/6);
        }break;
        
        case '\\':{
            stroke(255, 255, 0);
            strokeWeight(10);
            if(ar[I-1]){switch(ar[I-1][J].type){
                case '@':
                    line(0,0,-this.w/2,0);
                    ar[I-1][J].on=true;
                break;
                case '|':
                    if(ar[I-1][J].r===90||ar[I-1][J].r===270){
                        line(0,0,-this.w/2,0);
                        ar[I-1][J].on=true;
                    }
                break;
                case 'L':
                    if(ar[I-1][J].r===0||ar[I-1][J].r===90){
                        line(0,0,-this.w/2,0);
                        ar[I-1][J].on=true;
                    }
                break;
                case 'T':
                    if(ar[I-1][J].r!==90){
                        line(0,0,-this.w/2,0);
                        ar[I-1][J].on=true;
                    }
                break;
                case '+':
                    line(0,0,-this.w/2,0);
                    ar[I-1][J].on=true;
                break;
                case "'":
                    if(ar[I-1][J].r===90){
                        line(0,0,-this.w/2,0);
                        ar[I-1][J].on=true;
                    }
                break;
            }}
            if(ar[I+1]){switch(ar[I+1][J].type){
                case '@':
                    line(0,0,this.w/2,0);
                    ar[I+1][J].on=true;
                break;
                case '|':
                    if(ar[I+1][J].r===90||ar[I+1][J].r===270){
                        line(0,0,this.w/2,0);
                        ar[I+1][J].on=true;
                    }
                break;
                case 'L':
                    if(ar[I+1][J].r===180||ar[I+1][J].r===270){
                        line(0,0,this.w/2,0);
                        ar[I+1][J].on=true;
                    }
                break;
                case 'T':
                    if(ar[I+1][J].r!==270){
                        line(0,0,this.w/2,0);
                        ar[I+1][J].on=true;
                    }
                break;
                case '+':
                    line(0,0,this.w/2,0);
                    ar[I+1][J].on=true;
                break;
                case "'":
                    if(ar[I+1][J].r===270){
                        line(0,0,this.w/2,0);
                        ar[I+1][J].on=true;
                    }
                break;
            }}
            if(ar[I][J-1]){switch(ar[I][J-1].type){
                case '@':
                    line(0,0,0,-this.h/2);
                    ar[I][J-1].on=true;
                break;
                case '|':
                    if(ar[I][J-1].r===0||ar[I][J-1].r===180){
                        line(0,0,0,-this.h/2);
                        ar[I][J-1].on=true;
                    }
                break;
                case 'L':
                    if(ar[I][J-1].r===90||ar[I][J-1].r===180){
                        line(0,0,0,-this.h/2);
                        ar[I][J-1].on=true;
                    }
                break;
                case 'T':
                    if(ar[I][J-1].r!==180){
                        line(0,0,0,-this.h/2);
                        ar[I][J-1].on=true;
                    }
                break;
                case '+':
                    line(0,0,0,-this.h/2);
                    ar[I][J-1].on=true;
                break;
                case "'":
                    if(ar[I][J-1].r===180){
                        line(0,0,0,-this.h/2);
                        ar[I][J-1].on=true;
                    }
                break;
            }}
            if(ar[I][J+1]){switch(ar[I][J+1].type){
                case '@':
                    line(0,0,0,this.h/2);
                    ar[I][J+1].on=true;
                break;
                case '|':
                    if(ar[I][J+1].r===0||ar[I][J+1].r===180){
                        line(0,0,0,this.h/2);
                        ar[I][J+1].on=true;
                    }
                break;
                case 'L':
                    if(ar[I][J+1].r===0||ar[I][J+1].r===270){
                        line(0,0,0,this.h/2);
                        ar[I][J+1].on=true;
                    }
                break;
                case 'T':
                    if(ar[I][J+1].r!==0){
                        line(0,0,0,this.h/2);
                        ar[I][J+1].on=true;
                    }
                break;
                case '+':
                    line(0,0,0,this.h/2);
                    ar[I][J+1].on=true;
                break;
                case "'":
                    if(ar[I][J+1].r===0){
                        line(0,0,0,this.h/2);
                        ar[I][J+1].on=true;
                    }
                break;
            }}
            
            fill(255, 200, 0);
            stroke(0);
            strokeWeight(2);
            rectMode(CENTER);
            rect(0,0,this.w/4,this.h/2);
            rect(0,-this.h/6,this.w/6,this.h/3);
            fill(0);
            textSize((this.w<this.h?this.w:this.h)/10);
            textAlign(CENTER,CENTER);
            text("ON",0,this.h/6);
        }break;
        
        case '|':{
            
            stroke(this.on*255,this.on*255,0);
            strokeWeight(10);
            if(this.r===90||this.r===270){
                line(0,-this.w/2,0,this.w/2);
                this.left(ar,I,J);
                this.right(ar,I,J);
            }
            else{
                line(0,-this.h/2,0,this.h/2);
                this.down(ar,I,J);
                this.up(ar,I,J);
            }
        }break;
        
        case 'L':{
            
            stroke(this.on*255,this.on*255,0);
            strokeWeight(10);
            if(this.r===0){
                line(0,-this.h/2,0,0);
                line(0,0,this.w/2,0);
                this.up(ar,I,J);
                this.right(ar,I,J);
            }
            else if(this.r===90){
                line(0,-this.w/2,0,0);
                line(0,0,this.h/2,0);
                this.right(ar,I,J);
                this.down(ar,I,J);
            }
            else if(this.r===180){
                line(0,-this.h/2,0,0);
                line(0,0,this.w/2,0);
                this.down(ar,I,J);
                this.left(ar,I,J);
            }
            else{
                line(0,-this.w/2,0,0);
                line(0,0,this.h/2,0);
                this.left(ar,I,J);
                this.up(ar,I,J);
            }
        }break;
        
        case 'T':{
            stroke(this.on*255,this.on*255,0);
            strokeWeight(10);
            if(this.r===0){
                line(-this.w/2,0,this.w/2,0);
                line(0,0,0,this.h/2);
                this.right(ar,I,J);
                this.down(ar,I,J);
                this.left(ar,I,J);
            }
            else if(this.r===90){
                line(-this.h/2,0,this.h/2,0);
                line(0,0,0,this.w/2);
                this.down(ar,I,J);
                this.left(ar,I,J);
                this.up(ar,I,J);
            }
            else if(this.r===180){
                line(-this.w/2,0,this.w/2,0);
                line(0,0,0,this.h/2);
                this.left(ar,I,J);
                this.up(ar,I,J);
                this.right(ar,I,J);
            }
            else{
                line(-this.h/2,0,this.h/2,0);
                line(0,0,0,this.w/2);
                this.up(ar,I,J);
                this.right(ar,I,J);
                this.down(ar,I,J);
            }
        }break;
        
        case '+':{
            stroke(this.on*255,this.on*255,0);
            strokeWeight(10);
            if(this.r===0||this.r===180){
                line(-this.w/2,0,this.w/2,0);
                line(0,-this.h/2,0,this.h/2);
            }
            else{
                line(-this.h/2,0,this.h/2,0);
                line(0,-this.w/2,0,this.w/2);
            }
            this.up(ar,I,J);
            this.down(ar,I,J);
            this.left(ar,I,J);
            this.right(ar,I,J);
        }break;
        
        case "'":{
            stroke(this.on*255,this.on*255,0);
            strokeWeight(10);
            if(this.r===0||this.r===180){
                line(0,-this.h/2,0,0);
            }
            else{
                line(0,-this.w/2,0,0);
            }
        }break;
        
    }
    popMatrix();
    this.on=false;
};

//}

for(var i=0;i<levels.length;i++){
    cLevels.push(new level(
        levels[i].lev[0].length,
        levels[i].lev.length,
        levels[i]
    ));
}

var game= function() {
    cLevels[Level].all();
    switch(Level){
        case 0:
            clickHere(290,200);
        break;
        case 1:
            clickHere(290,200);
        break;
        case 2:
            clickHere(370,200);
        break;
        case 5:
            clickHere(290,200);
            clickHere(160,550);
        break;
        case 6:
            clickHere(450,550);
        break;
    }
    //level completion and overall win{
    fill(0,win);
    win+=5;
    if(win>255){
        Level++;
        win='_';
        frameCount=0;
    }
    rectMode(CORNER);
    rect(0,0,500,600);
    if(Level===levels.length-1){
        background(0);
        rain.all();
        fill(255, frameCount);
        textSize(50);
        textAlign(CENTER,CENTER);
        text("YOU WIN!",260,300);
    }
    //}
};

var scene="home";
var cols=[
    
    [color(random(200),random(255),random(100)),
    color(random(200),random(255),random(100)),
    color(random(200),random(255),random(100)),
    color(random(200),random(255),random(100)),
    color(random(200),random(255),random(100)),],
    
    [color(random(200),random(255),random(100)),
    color(random(200),random(255),random(100)),
    color(random(200),random(255),random(100)),
    color(random(200),random(255),random(100)),
    color(random(200),random(255),random(100)),
    color(random(200),random(255),random(100)),
    color(random(200),random(255),random(100)),
    color(random(200),random(255),random(100)),
    color(random(200),random(255),random(100)),
    color(random(200),random(255),random(100)),
    color(random(200),random(255),random(100)),
    color(random(200),random(255),random(100)),],
    
    [color(random(200),random(255),random(100)),
    color(random(200),random(255),random(100)),
    color(random(200),random(255),random(100)),
    color(random(200),random(255),random(100)),
    color(random(200),random(255),random(100)),
    color(random(200),random(255),random(100)),
    color(random(200),random(255),random(100)),
    color(random(200),random(255),random(100)),
    color(random(200),random(255),random(100)),
    color(random(200),random(255),random(100)),
    color(random(200),random(255),random(100)),]
    
];

draw=function(){
    background(100);
    switch(scene){
        case "home":{
            rain.all();
            fill(100,100);
            rectMode(CENTER);
            rect(250,300,500,600);
            textAlign(CENTER,CENTER);
            textSize(50);
            for(var i=0;i<5;i++){
                fill(cols[0][i]);
                text("WIRES"[i],170+i*40,80+sin(frameCount/5+i*500)*10);
            }
            textSize(30);
            for(var i=0;i<12;i++){
                fill(cols[1][i]);
                text("an INTUITIVE"[i],130+i*20,180+sin(frameCount/5+i*500)*5);
            }
            for(var i=0;i<11;i++){
                fill(cols[2][i]);
                text("puzzle game"[i],130+i*20,230+sin(frameCount/5+i*500)*5);
            }
            fill(255);
            stroke(255, 0, 0);
            rectMode(CENTER);
            inPlay=dist(mouseX,mouseY,250,350)<75;
            ellipse(250,350,
                150+(inPlay?sin(frameCount/10)*10:0),
                150+(inPlay?cos(frameCount/10)*10:0)
            );
            fill(255, 0, 0);
            text("PLAY",250,350);
        }break;
        case "game":
            game();
        break;
    }
};

mouseClicked=function(){
if(scene==="game"){
    for(var i=0;i<cLevels[Level].pieces.length;i++){
        for(var j=0;j<cLevels[Level].pieces[i].length;j++){
            var x=cLevels[Level].pieces[i][j].x;
            var y=cLevels[Level].pieces[i][j].y;
            var w=cLevels[Level].pieces[i][j].w;
            var h=cLevels[Level].pieces[i][j].h;
            if(mouseX>x&&mouseY>y&&mouseX<x+w&&mouseY<y+h){
                cLevels[Level].pieces[i][j].click();
            }
        }
    }
    if(mouseY>500){
        if(mouseX<60){
            sel=0;
        }
        else if(mouseX<130){
            sel=1;
        }
        else if(mouseX<200){
            sel=2;
        }
        else if(mouseX<300){
            sel=3;
        }
        else if(mouseX<370){
            sel=4;
        }
        else if(mouseX<440){
            sel=5;
        }
        else{
            sel=6;
        }
    }
}
    else{if(inPlay){scene="game";}
        
    }
    
};

/* jshint ignore:end */

//}



    }};

  // Get the canvas that ProcessingJS will use
  var canvas = document.getElementById("mycanvas"); 
  // Pass the function to ProcessingJS constructor
  var processingInstance = new Processing(canvas, programCode); 
  </script>
</html>
