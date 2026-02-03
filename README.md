<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Snapchat Call UI</title>

<style>
body{
    margin:0;
    height:100vh;
    display:flex;
    align-items:center;
    justify-content:center;
    background:#111;
    font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,sans-serif;
}

.phone{
    width:360px;
    height:720px;
    background:#f7d046;
    border-radius:40px;
    box-shadow:0 20px 60px rgba(0,0,0,0.5);
    position:relative;
    overflow:hidden;
}

/* Screens */
.screen{
    position:absolute;
    width:100%;
    height:100%;
    transition:opacity .4s ease;
}

.hidden{
    opacity:0;
    pointer-events:none;
}

/* Call UI */
.top-bar{
    padding:20px;
    text-align:center;
    font-weight:600;
    color:#222;
}

.avatar-container{
    position:absolute;
    top:45%;
    left:50%;
    transform:translate(-50%,-50%);
    text-align:center;
}

.shadow-avatar{
    width:160px;
    height:160px;
    border-radius:50%;
    background:radial-gradient(circle,#222 40%,#000 70%);
    animation:pulse 2s infinite;
}

@keyframes pulse{
    0%{box-shadow:0 0 0 0 rgba(0,0,0,.5);}
    70%{box-shadow:0 0 0 20px rgba(0,0,0,0);}
    100%{box-shadow:0 0 0 0 rgba(0,0,0,0);}
}

.caller-name{
    margin-top:25px;
    font-size:22px;
    font-weight:700;
}

.calling-text{
    font-size:14px;
    color:#444;
}

.bottom-controls{
    position:absolute;
    bottom:40px;
    width:100%;
    display:flex;
    justify-content:space-around;
}

.btn{
    width:70px;
    height:70px;
    border-radius:50%;
    display:flex;
    align-items:center;
    justify-content:center;
    font-size:28px;
    color:white;
    cursor:pointer;
}

.decline{background:#ff3b30;}
.accept{background:#34c759;}

/* Message Screen */
.message-screen{
    display:flex;
    align-items:center;
    justify-content:center;
    padding:30px;
    text-align:center;
}

.message-box{
    background:rgba(0,0,0,0.1);
    padding:25px;
    border-radius:20px;
    font-size:18px;
    font-weight:600;
    line-height:1.5;
}

/* GLITCH EFFECT */
.glitch{
    position:absolute;
    top:0;
    left:0;
    width:100%;
    height:100%;
    background:#000;
    color:#ff2b2b;
    display:flex;
    align-items:center;
    justify-content:center;
    font-size:42px;
    font-weight:900;
    letter-spacing:3px;
    text-transform:uppercase;
    animation:glitchAnim 0.7s linear infinite;
    z-index:10;
}

@keyframes glitchAnim{
    0%{transform:translate(0,0);}
    20%{transform:translate(-5px,5px);}
    40%{transform:translate(5px,-5px);}
    60%{transform:translate(-5px,-5px);}
    80%{transform:translate(5px,5px);}
    100%{transform:translate(0,0);}
}
</style>
</head>

<body>

<div class="phone">

    <!-- Call Screen -->
    <div id="callScreen" class="screen">
        <div class="top-bar">Incoming Call</div>

        <div class="avatar-container">
            <div class="shadow-avatar"></div>
            <div class="caller-name">Unknown popchatter</div>
            <div class="calling-text">Snapchat Audio Call…</div>
        </div>

        <div class="bottom-controls">
            <div class="btn decline" onclick="declineCall()">✕</div>
            <div class="btn accept" onclick="answerCall()">✓</div>
        </div>
    </div>

    <!-- Message Screen -->
    <div id="messageScreen" class="screen hidden message-screen">
        <div class="message-box">
            Rogan! I know you are so confused but you need to understand…<br><br>
            the weird sounds on your walkie talkie and the weird sounds you've been hearing is Shadow.
            You need to get out of there now.<br><br>
            I am you from the future!
        </div>
    </div>

</div>

<script>
function answerCall(){
    document.getElementById('callScreen').classList.add('hidden');
    document.getElementById('messageScreen').classList.remove('hidden');
}

function declineCall(){
    const glitch = document.createElement("div");
    glitch.className = "glitch";
    glitch.innerText = "WRONG CHOICE!";
    document.querySelector(".phone").appendChild(glitch);

    setTimeout(()=>{
        glitch.remove();
    },2000);
}
</script>

</body>
</html>
