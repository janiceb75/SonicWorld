<div class="design">

<center>

<p style="0px">Name</p>
<select bind:value={userName}> 
<option value="sonic">Sonic</option>
<option value="shadow">Shadow</option>
<option value="tails">Tails</option>
<option value="silver">Silver</option>
<option value="knuckles">Knuckles</option>
</select>
<br>
<p>Ability</p>
<select bind:value={userAbility}>
<option value="speed">Speed</option>
<option value="strength">Strength</option>
<option value="flying">Flying</option>
<option value="chaos control">Chaos Control</option>
<option value="rollerskating">Roller Skating</option>
</select>
<br><br>
<button on:click={sonicCreate}>Let's Go!</button>
<br>



<!-- <button on:click={changePic}>Show Me My Character!</button> -->

<br>

<p style= "color:{ansColor}; font-size:25px">{answer}</p>
<br>

<p><img style="width:200px; height:300px" src={pic}/></p>
</center>
</div>

<p style="color: blue; font-size: 24px; font-weight: bold; display: {showPowerLabel && 'block' || 'none'};">
    Do You Want Powers?
</p>





    


<!-- if (showPowerLabel=="true"){
    <p>Do You Want Powers?</p>
    
    } -->


<style>

.design{
    border-radius: 20px;
    border-color: blue;
    border-width: 2px;
    border-style: solid;
    padding:8px;
    color:blue;
    background-color: silver;
    height:180px;
    max-width: 400px;
    box-shadow: 10px 5px 5px blue;
    position: relative;
    transform:translateX(-50%);
    left:50%;
    
    /* width: 800px; */
    
}

</style>

<script>
  import { get } from "svelte/store";

    //create a label called name and a text field underneath
    //create a label called ability and a text field underneath
    //bind the first text field to a variable called userName
    //bing the second text field to a varaiable called userAbility
    let userName;
    let userAbility;
    let answer;
    let pic;
    let ansColor;
    let sound;
    let showPowerLabel = false; // Initially hidden

    // function changePic(){

    //     if(userName =="sonic" && userAbility == "speed"){
    //         pic = "https://www.google.com/imgres?q=sonic&imgurl=https%3A%2F%2Fstatic.wikia.nocookie.net%2Fgreat-characters%2Fimages%2Fa%2Fa7%2FSXSG_Sonic.png%2Frevision%2Flatest%3Fcb%3D20240715054611&imgrefurl=https%3A%2F%2Fgreat-characters.fandom.com%2Fwiki%2FSonic_the_Hedgehog&docid=6BPK9cXRftKY5M&tbnid=lZGgt7NWBEKDMM&vet=12ahUKEwjm9JjNn-CLAxVZv4kEHS65FVAQM3oECBcQAA..i&w=800&h=1200&hcb=2&ved=2ahUKEwjm9JjNn-CLAxVZv4kEHS65FVAQM3oECBcQAA"
    //     }
    // }

    function getPower()
    {
        showPowerLabel = true;//make label appear

    }

    function sonicCreate(){
        userName = userName.toLowerCase();
        userAbility = userAbility.toLowerCase();
        sound="";
        if (userName =="sonic" && userAbility == "speed")
        { answer = "I'm Sonic!"
          pic = "https://pngimg.com/uploads/sonic_hedgehog/sonic_hedgehog_PNG17.png";
          ansColor="green";
          sound = new Audio("/sounds/sonic-youre-too-slow.mp3").play();
          setTimeout(getPower, 2000);
         
          //then i want a button to appear to say do you want power? 
          //i feel like this should be a function
          //if the user says yes, then it will ask them to select a challenge
          //if math then it will give 3 questions and each one get a ring to appear
          //if color challenge it will ask 3 questions like what does red and blue make
          //for each right one they get a ring
          //at the end if they get all 3 rings they get super powers
          //if 2 then ok powers
          //if one then minimal power
          //if none, sorry try again
        }
        else if (userName =="knuckles" && userAbility == "strength")
        {
           answer = "Hi Knuckles"
           pic = "https://www.pngmart.com/files/13/Knuckles-The-Echidna-PNG-Photos.png";
           ansColor="green";
           sound= new Audio("/sounds/all-got-101soundboards.mp3").play();
        }
        else if (userName == "silver" && userAbility == "chaos control")
        {
            answer = "I'm Silver!"
            pic = "https://www.pngmart.com/files/13/Silver-The-Hedgehog-PNG-Picture.png";
            ansColor="green";
            sound = new Audio("/sounds/silver.mp3").play();
        }
        else if (userName == "tails" && userAbility == "flying")
        {
            answer = "I'm Tails!"
            pic = "https://www.pngmart.com/files/13/Tails-PNG-Photo.png";
            ansColor="green";
            sound = new Audio("/sounds/miles.mp3").play();
        }
        else if (userName == "shadow" && userAbility =="rollerskating")
        {
            answer = "I'm Shadow!"
            pic = "https://www.pngmart.com/files/13/Shadow-The-Hedgehog-PNG-Clipart.png";
            ansColor="green";
            sound = new Audio("/sounds/shadow.mp3").play();
        } else
        {
            answer = "Sorry, try again!"
            pic ="https://www.pngmart.com/files/8/Crying-Emoji-PNG-Transparent-Images.png";
            ansColor="red";
            sound = new Audio("/sounds/fail.mp3").play();
        }

//With separate if statements: If "sonic" is entered, all if conditions are still checked, including the last one, which means else could override a correct answer.
// With else if: As soon as a match is found, the rest are skipped, preventing unwanted overrides.
    }

</script>