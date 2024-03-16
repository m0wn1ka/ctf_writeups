## beginer/gauntlet
## question
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/a1d4e6e3-3708-4b5d-b561-8fc00dfebf27)
- this is the page
![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/5f10c99c-43c6-435c-b3eb-2485a6d759aa)
- at bottom we see a commetn
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/20874902-ae18-4160-8764-275b82864fb8)
- on going to that page  https://gauntlet-okntin33tq-ul.a.run.app/hidden9136234145526
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/b56c3b84-0e7f-4bae-b018-6b641b965584)
- we try to see if there is something in the souce code
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/54e8ab9e-27bc-49cf-8528-51c4affca63b)
- so we do send with such request header
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/09c0a3a1-640c-4090-a57d-614e2b528fbd)
- now we go thre https://gauntlet-okntin33tq-ul.a.run.app/hidden0197452938528
- now it says change metod
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/7cff3520-f7af-4087-94b4-bb5ed2311811)
- now we chagne request methods ,try post,put ,options
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/e671b26e-1ed9-44af-8683-1b2b9d3e5633)
- now go here https://gauntlet-okntin33tq-ul.a.run.app/hidden5823565189534225
- now with this url we get https://gauntlet-okntin33tq-ul.a.run.app/hidden5823565189534225?wolvsec=c%23%2Bl
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/7edaeb2c-fb9a-4427-8464-34a5167a0abe)
- so now we go thre https://gauntlet-okntin33tq-ul.a.run.app/hidden5912455200155329
- NOW we do the need ful
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/1d45d40f-7eb0-4d9b-96a9-4e4825054540)
- now we go to page 5 https://gauntlet-okntin33tq-ul.a.run.app/hidden3964332063935202
- here on page 5 viewing source code does not give us the path but on inspection we get it
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/06dbd3a0-0c86-4d3c-95d1-2d3d7b1960a1)
- now page6 https://gauntlet-okntin33tq-ul.a.run.app/hidden5935562908234557
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/91362751-fd36-4236-9fc5-dd28c73cbe17)
- there happens redirections
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/c76af2c1-2582-4177-915b-ab5d9b59234b)
- now page 7 https://gauntlet-okntin33tq-ul.a.run.app/hidden82008753458651496
- now page 7 is this
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/ec8e8da2-1c20-4000-bb05-4bf7029714e2)
- we change cookie value
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/5eecafe8-a76c-49e9-b70a-5835e2d83294)
- now page 8 https://gauntlet-okntin33tq-ul.a.run.app/hidden00127595382036382
- this is page 8 ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/c5ef745a-590e-485c-8dfe-465633c280ea)
- we decode the jwt in jwt.io
- if there is  no check on signature we can move forward easily
- now we use the given secret
- ![image](https://github.com/m0wn1ka/ctf_writeups/assets/127676379/6fa17377-9f3d-491e-af58-fc06d6ef0c4b)
- now page 9
- https://gauntlet-okntin33tq-ul.a.run.app/hidden83365193635473293


