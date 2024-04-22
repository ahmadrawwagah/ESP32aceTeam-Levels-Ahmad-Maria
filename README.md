# ESP32aceTeam

SpaceTeam for ESP32s

Designed by Eliana Shapere
https://docs.google.com/document/d/1vphklPqY_keQlNk1hVz_C3Pq45uIHXlx6fpNlm-N9_k/edit

# Assignment

**Goal:** Add levels - each level should feature more difficult actions (perhaps using extended ascii characters)

**Usage:** When the user joins the game, they must do one of the following three optins:
  1) Press the right button for level 3
  2) Press the left button for level 2
  3) Wait 5 seconds for the game to default to level 1

**Level 1 dictionary:**

const String commandVerbs1[ARRAY_SIZE] = {"Buzz", "Engage", "Floop", "Bother", "Twist", "Jingle", "Jangle", "Yank", "Press", "Play"};

const String commandNounsFirst1[ARRAY_SIZE] = {"foo", "dev", "bobby", "jaw", "tooty", "wu", "fizz", "rot", "tea", "bee"};

const String commandNounsSecond1[ARRAY_SIZE] = {"bars", "ices", "pins", "nobs", "zops", "tangs", "bells", "wels", "pops", "bops"};

**Level 2 dictionary:**

const String commandVerbs2[ARRAY_SIZE] = {"Bu#zz", "Eng@age", "Flo%op", "Bot&her", "Twist", "Jin'gle", "Ja.ngle", "Yan?k", "P\ress", "Pl/ay"};

const String commandNounsFirst2[ARRAY_SIZE] = {"f=oo", "de-v", "bob_by", "j(aw", "too)ty", "wu", "fizz", "ro[t", "te{a", "be]e"};

const String commandNounsSecond2[ARRAY_SIZE] = {"ba/rs", "ice>s", "pi<ns", "n,obs", "zo]ps", "tan[gs", "bel=ls", "3els", "p4ops", "bop5s"};

**Level 3 dictionary:**

const String commandVerbs3[ARRAY_SIZE] = {"@","#","!", "%","^", "&","*", "(",")", "_"};

const String commandNounsFirst3[ARRAY_SIZE] = {"+","|","}","{",";",":","{","-","=","\\"};

const String commandNounsSecond3[ARRAY_SIZE] = {"'", "/","?", ".",",", "<",">", "~","`", "8"};

**Code Changes:**

Added a setup function in order to handle setting the level at the beginning of runtime. Functionality is as explained above.
```
void levelSetup(){
  int start_time = millis();
  while(true){
    if ((millis() - start_time) > 5000)
    {
      level = 1;
      expireLength = expireLength1;
      break;
    }
    else if (scheduleCmd1Send){
      level = 2;
      expireLength = expireLength2;
      break;
    }
    else if(scheduleCmd2Send){
      level = 3;
      expireLength = expireLength3;
      break;
    }

  }
}
```



