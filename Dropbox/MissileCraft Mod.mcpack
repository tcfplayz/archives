/*MissileCraft Mod*/
/*By: Andr3w246*/
/*COPYRIGHT ANDR3W246 (c) 2015*/

//Variables
var version= "0.3alpha"
var setX= 0
var setY= 0
var setZ= 0
var set2X= 0
var set2Y= 0
var set2Z= 0
var targetSet= 0
var targetSet2= 0
var launchX= 0
var launchY= 0
var launchZ= 0
var addY= 0
var subY= 50
var add2Y= 0
var sub2Y= 50
var launchSet= 0
var iron= "iron_block"
var inAir= 0
var mTick= 0
var ud= 0
var mid= 0
var fTicks= 0

//New Blocks
Block.defineBlock(23, "Launch Platform", ["iron_block", 0], 1, false, 0);
Block.setDestroyTime(23, 5);
Block.setLightOpacity(23, 0);
Block.setColor(23, [0x555555]);
Block.setShape(23, 0, 0, 0, 1, 0.5, 1);
Block.defineBlock(25, "Launch Control Panel", [["redstone_block", 0],["redstone_block", 0],["stone", 0],["stone", 0],["stone", 0],["stone", 0]], 1, false, 0);
Block.setDestroyTime(25, 5);
Block.setLightOpacity(25, 0);
Block.setShape(25, 0.25, 0, 0.25, 0.75, 1, 0.75);
Block.defineBlock(28, "Conventional Missile", [["redstone_block",0],["obsidian",0],[iron,0],[iron,0],[iron,0],[iron,0]], 20, false, 0);
Block.setDestroyTime(28, 0.1);
Block.setLightOpacity(28, 0);
Block.setShape(28, 0.1, -0.5, 0.1, 0.9, 1.25, 0.9);
Block.defineBlock(29, "Breaching Missile", [["redstone_block",0],["tnt",0],[iron,0],[iron,0],[iron,0],[iron,0]], 20, false, 0);
Block.setDestroyTime(29, 0.1);
Block.setLightOpacity(29, 0);
Block.setShape(29, 0.1, -0.5, 0.1, 0.9, 1.5, 0.9);
Block.defineBlock(33, "Nuclear Missile", [["redstone_block",0],["emerald_block",0],[iron,0],[iron, 0],[iron,0],[iron,0]], 20, false, 0);
Block.setDestroyTime(33, 0.1);
Block.setLightOpacity(33, 0);
Block.setShape(33, 0.1, -0.5, 0.1, 0.9, 2.5, 0.9);
Block.defineBlock(34, "Thermobaric Missile", [["redstone_block",0],["diamond_block",0],[iron,0],[iron,0],[iron,0],[iron,0]], 20, false, 0);
Block.setDestroyTime(34, 0.1);
Block.setLightOpacity(34, 0);
Block.setShape(34, 0.1, -0.5, 0.1, 0.9, 3, 0.9);
Block.defineBlock(36, "Ender Missile", [["redstone_block",0],["soul_sand",0],[iron,0],[iron,0],[iron,0],[iron,0]], 20, false, 0);
Block.setDestroyTime(36, 0.1);
Block.setLightOpacity(36, 0);
Block.setShape(36, 0.1, -0.5, 0.1, 0.9, 2, 0.9);
Block.defineBlock(55, "Napalm Missile" ,[["redstone_block",0],["wool",1],[iron,0],[iron,0],[iron,0],[iron,0]], 20, false, 0);
Block.setDestroyTime(55, 0.1);
Block.setLightOpacity(55, 0);
Block.setShape(55, 0.1, -0.5, 0.1, 0.9, 2, 0.9);

//New Items
ModPE.setItem(500, "blaze_rod", 0, "Position Definer");
ModPE.setItem(501, "item_frame", 0, "Missile Platform Maker");

function useItem(x, y, z, itemId, blockId, side){
if(itemId==500&&blockId==23){
launchX= x
launchY= y
launchZ= z
launchSet= 1
clientMessage("§2Launch Platform set!");
}
if(itemId==500&&launchSet!=1&&blockId!=23){
clientMessage("§4Launch Platform not set! Please tap this item on one to set it!");
}
if(itemId==500&&launchSet==1&&blockId!=23&&blockId!=25){
setX= x
setY= y
setZ= z
targetSet= 1
clientMessage("§2Target set to [X: "+setX+",Y: "+setY+",Z: "+setZ+"]");
}
if(blockId==25){
var check= Level.getTile(x, y+1, z+1);
if (check!=0&&targetSet==1){
inAir= 1
addY= launchY+1
mid= check
Level.setTile(launchX, launchY+1, launchZ, 0);
clientMessage("Missile Launched!");
}
if(targetSet==0){
clientMessage("§4No Target set! Please set a target with the position definer!");
}
if(check!=28&&check!=29&&check!=33&&check!=34&&check!=36&&check!=55){
clientMessage("§4No Missile loaded!");
}
if(launchSet!=1){
clientMessage("§4No set Launch Platform!");
}
}
if(itemId==501){
Level.setTile(x, y+1, z, 25);
Level.setTile(x, y+1, z+1, 23);
}
if(itemId==23||itemId==25){
preventDefault();
clientMessage("§6You cannot place this block down.");
}
if(itemId==500&&blockId==25){
clientMessage("Please do not tap the launcher with the position definer!");
}
}

function newLevel(){
clientMessage("MissileCraft Mod Ver: §6"+version);
clientMessage("By: §6Andr3w246");
clientMessage("ONLY USE THIS MOD IN CREATIVE!");
Player.addItemCreativeInv(28, 1, 0);
Player.addItemCreativeInv(29, 1, 0);
Player.addItemCreativeInv(33, 1, 0);
Player.addItemCreativeInv(34, 1, 0);
Player.addItemCreativeInv(36, 1, 0);
Player.addItemCreativeInv(55, 1, 0);
Player.addItemCreativeInv(500, 1, 0);
Player.addItemCreativeInv(501, 1, 0);
}

function modTick(){
if(inAir==1){
mTick++
if(mTick==5&&fTicks!=50&&ud==0){
mTick= 0
addY++
fTicks++
Level.setTile(launchX, addY-1, launchZ, 0);
Level.setTile(launchX, addY, launchZ, mid);
Level.addParticle(ParticleType.cloud, launchX+0.5, addY-1.25, launchZ+0.5, 0, 0, 0, 500);
Level.addParticle(ParticleType.cloud, launchX+0.5, addY-1.25, launchZ+0.5, 0, 0, 0, 500);
}
if(mTick==5&&fTicks==50){
mTick= 0
Level.setTile(launchX, addY, launchZ, 0);
addY= 0
fTicks= 0
ud= 1
}
if(mTick==5&&subY!=0&&ud==1){
mTick= 0
subY--
Level.setTile(setX, setY+subY+1, setZ, 0);
Level.setTile(setX, setY+subY, setZ, mid);
}
if(mTick==5&&subY==0){
mTick= 0
inAir= 0
ud= 0
subY= 50
Level.setTile(setX, setY+subY, setZ, 0);
if(mid==28){
explode(setX+0.5, setY, setZ+0.5, 10);
}
if(mid==29){
explode(setX+0.5, setY, setZ+0.5, 5);
explode(setX+0.5, setY-2.5, setZ+0.5, 5);
explode(setX+0.5, setY-5, setZ+0.5, 5);
explode(setX+0.5, setY-7.5, setZ+0.5, 5);
explode(setX+0.5, setY-10, setZ+0.5, 5);
}
if(mid==33){
explode(setX+0.5, setY, setZ+0.5, 50);
}
if(mid==34){
explode(setX+0.5, setY, setZ+0.5, 250);
explode(setX+12.5, setY, setZ+0.5, 250);
explode(setX-12.5, setY, setZ-0.5, 250);
explode(setX+0.5, setY, setZ+12.5, 250);
explode(setX-0.5, setY, setZ-12.5, 250);
}
if(mid==36){
explode (setX+0.5, setY, setZ+0.5, 15);
for(a=0; a<20; a++){
for(b=0; b<20; b++){
for(c=0; c<20; c++){
var ran= Math.random()*100
if(ran>=95){
Level.setTile(setX-10+a, setY-10+b, setZ-10+c, 121);
}
}}}
}
if(mid==55){
explode(setX+0.5, setY, setZ+0.5, 10);
for(a=0; a<30; a++){
for(b=0; b<30; b++){
for(c=0; c<30; c++){
var ran= Math.random()*100
if(ran>=70){
var check1= Level.getTile(setX-15+a, setY-15+b, setZ-15+c);
var check2= Level.getTile(setX-15+a, setY-16+b, setZ-15+c);
if(check1==0&&check2!=0&&check2!=51){
Level.setTile(setX-15+a, setY-15+b, setZ-15+c, 51);
}
}
}}}
}
targetSet= 0
}
}
}
