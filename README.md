<canvas id="mycanvas" height="200" width="200"></canvas>
<script type="text/javascript">
    function drawTree() {
        // get the canvas element using the DOM
        var canvas = document.getElementById('mycanvas');
 
        // Make sure we don't execute when canvas isn't supported
        if (canvas.getContext) {
            // use getContext to use the canvas for drawing
            var ctx = canvas.getContext('2d');
 
            //back
            ctx.fillStyle = "green";
            ctx.fillRect(60, 50, 40, 90);
            ctx.fillRect(40, 110, 80, 40);
 
            //leaves
            a = 60;
            b = 10;
            for (var i = 0; i < 4; i++) {
                drawLeaf(-20 + a - (i * 10), b + (i * 30), ctx, "left");
                drawLeaf(20 + a + (i * 10), b + (i * 30), ctx, "right");
            }
 
            //stump
            ctx.fillStyle = "brown";
            ctx.fillRect(70, 120, 20, 40);
 
            //star
            drawStar(ctx, 80, 20, 20, 5, 0.5);
 
        } else {
            alert('You need Safari or Firefox 1.5+ to see this demo.');
        }
    }
 
    function drawLeaf(x, y, ctx, style) {
        // Right Filled triangle
        ctx.beginPath();
        ctx.fillStyle = "green";
        if (style == "right") {
            ctx.moveTo(x, y);
            ctx.lineTo(x + 40, y + 40);
            ctx.lineTo(x, y + 40);
        } else {
            ctx.moveTo(x + 40, y);
            ctx.lineTo(x, y + 40);
            ctx.lineTo(x + 40, y + 40);
        }
        ctx.fill();
    }
 
    function drawStar(ctx, x, y, r, p, m) {
        ctx.fillStyle = "gold";
        ctx.beginPath();
        ctx.translate(x, y);
        ctx.moveTo(0, 0 - r);
        for (var i = 0; i < p; i++) {
            ctx.rotate(Math.PI / p);
            ctx.lineTo(0, 0 - (r * m));
            ctx.rotate(Math.PI / p);
            ctx.lineTo(0, 0 - r);
        }
        ctx.fill();
        ctx.restore();
    }
window.setTimeout(drawTree, 1000);
</script>
