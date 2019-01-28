# -JAVASCRIPT---DM-Ereaser-
 DISCORD CONSOLE


M
Method Does not require any running program.

This is Script you can put in the console. 

Make sure your looking at the DM or channel(If you want to delete your message).




//Discord DM Eraser [Important Note: you'll need the DM open until it finishes for it to work properly.]
//Version:
//Author:
//Paste the code as-is into discord console, and it will proceed to delete any messages (that you can delete) in the DM (or any channel for that matter)
var cont;
var opts;
var option;
function scanMessage(delay, i){
    if(!i)
        i = 0;
 
    //Search options
    opts = document.querySelectorAll("div[class*='messages'] div[class*='message-'] div[class*='buttonContainer'] div[class*='button-']");
 
    //skip cycle flag
    cont = false;
 
    //Open options, check for end of channel
    var loadMore = document.querySelector("div[class*='messages'] div[class*='hasMore-'] button");
    var endOfMess = document.querySelector("div[class*='messages-'] div[class*='default-'][class*='base-']");
    option = opts[i];
 
    //Load more if there are more messages.
    if(!option && i != 0){
        if(endOfMess || !loadMore)
            return console.log("Finished.");
        loadMore.click();
        console.clear();
        console.log("Loading more..");
        return scanMessage(delay, 0);
    }
 
    if(!option)
        return console.log("Finished.");
 
    //Click option
    option.click();
 
    //Click delete option, if it's your own message.
    setTimeout(function(){
        var del = document.querySelector("div[class*='theme-dark'] div[class*='popout-'] button:last-of-type");
        if(del && del.innerText.indexOf("Delete") != -1){
            del.click();
            cont = true;
        }
    }, 50);
 
    //Click delete button.
    setTimeout(function(){
        var del = document.querySelector("button[class*='colorRed']");
        if(cont){
            del.click();
            setTimeout(scanMessage, delay, delay, i);
        }else{
            console.log("Skipping..");
            setTimeout(scanMessage, 1, delay, i + 1);
        }
    }, 100);
}
scanMessage(1600);
/

 
