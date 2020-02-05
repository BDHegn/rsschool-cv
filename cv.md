## rsschool-summary
# Artem Rumachik
### Contacts
> E-mail: AvPspace@gmail.com

> Phone: +397 29 279-48-75

### Task
> To acquire knowledge and experience in frontend development for making perspective carrier and be professional in this field.
## Skills

### Computer skills:

* C#, Delphi programming languages
* HTML5,CSS,JS
* UI design skills in Adobe Photoshop, Adobe Illustrator, Corel Draw, Adobe Animate
* Ability to work with 3Ds Max, AutoCad
* Knowledge of working with DB

### Languages skills:

* Russian
* Belarusian
* English

### Example of latest code:

> Here is a small piece of code for my game on JS.


```
var game = {
    ctx: undefined,
    platform: undefined,
    ball : undefined,
    width:640,
    heigth:320,
    rows:8,
    cols:10,
    running: true,
    score:0,
    blocks: [],
    sprites:{
        background: undefined,
        platform: undefined,
        ball: undefined,
        block:undefined
    },
    init: function(){
        var canvas = document.getElementById("mycanvas");
        this.ctx = canvas.getContext("2d");

        window.addEventListener("keydown",function(e){
            if(e.keyCode == 65)
            {
                game.platform.dx = -game.platform.velocity
            } else if(e.keyCode == 68)
            {
                game.platform.dx = game.platform.velocity
            } else if(e.keyCode == 32)
            {
                game.platform.releaseBall();
            }
        });
        window.addEventListener("keyup",function(e){
            game.platform.stop();
        });
        this.ctx.font = "20px Arial";
        this.ctx.fillStyle = "#fff";
    },
    load: function(){
        for (var key in this.sprites){
            this.sprites[key]=new Image();
            this.sprites[key].src = "img/"+key+".png";
        }
    },
    create:function(){
        for (var row=0; row<this.rows; row++)
        {
            for (var col=0; col<this.cols; col++)
            {
                this.blocks.push({
                    x:54 * col + 50,
                    y:15 * row + 35,
                    width:51,
                    heigth:14,
                    isAlive: true,
                });
            }
        }    
    },
     start: function(){
        this.init();
        this.load();
        this.create();
        this.run();
     },
     render:  function(){
        this.ctx.clearRect(0,0,this.width,this.heigth);
        this.ctx.drawImage(this.sprites.background,0,0);
        this.ctx.drawImage(this.sprites.platform,this.platform.x,this.platform.y);
        this.ctx.drawImage(this.sprites.ball,this.ball.x*this.ball.frame,0,this.ball.width,this.ball.heigth,this.ball.x,this.ball.y,this.ball.width,this.ball.heigth); 
        
        this.blocks.forEach(function(element)
        {
            if(element.isAlive)
            {
        this.ctx.drawImage(this.sprites.block,element.x,element.y); 
            }
        },this);

        this.ctx.fillText("Score:"+this.score,15,this.heigth-15);
    },
    update:function(){

        if(this.ball.collide(this.platform)){
            this.ball.bumpPlatform(this.platform);
        }


        if(this.platform.dx)
        {
            this.platform.move();
        }
        if(this.ball.dx || this.ball.dy)
        {
            this.ball.move();
        }
        this.blocks.forEach(function(element){
            if(element.isAlive){
                if(this.ball.collide(element)){
                    this.ball.bumpBlock(element);
                }
            }
        },this);

        this.ball.checkBounds();
    },
     run: function(){
        this.update(); 
        this.render();
        if(this.running){
            window.requestAnimationFrame(function(){
                game.run();
            });
        }
     },
     over:function(message){
         alert(message);
        this.running=false;
        window.location.reload();
     }
};
```

## Education

* Student of Minsk College of Bussines (2017-2020)
* High school №84(2007-2016)
