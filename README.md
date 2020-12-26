# brew906.github.io
this is a page i made at my school to learn coding
<!DOCTYPE html>
<!--created by Michael Brewer
Sep.17,2020
micbrewe@uat.edu-->
<html>

<head>
    <!--this links the js and css files with the code in them-->
    <script src="UATBlastoffcode.js"></script>
    <script src="class.js"></script>
    <link href="BlastoffPageStyle.css" rel="stylesheet" type="text/css" />
    <script src="dataLoader.js"></script>
    <title>
        Uat space program Count Down
    </title>
    <script>
        //needed variables
        var theTime = new Date();
        var tempTime = new Date();
        var time_interval = 5000;
        var last_iteration =0;
        var running = true;
        var index = 0;
        var timer;

        //load our data
        var data = getData();

        function updateDisplay(){
            theTime = new Date();

            //debuggin
            console.log("Display: " + (theTime.getHours() < 10 ? "0" + theTime.getHours() : theTime.getHours()) + ":" + 
            (theTime.getMinutes() < 10 ? "0" + theTime.getMinutes() : theTime.getMinutes()) + ":" + 
            (theTime.getSeconds() < 10 ? "0" + theTime.getSeconds() : theTime.getSeconds()));
            
                       
            var timeRead = data[index].time_seconds;

            if (timeRead >= 10){
                // TODO update the table
                document.getElementById("data").rows["seconds"].innerHTML = dataRow("Time Elapsed", data[index].time_seconds, "seconds");
                document.getElementById("data").rows["latitude"].innerHTML = dataRow("Latitude", data[index].latitude, " ");
                document.getElementById("data").rows["longitude"].innerHTML = dataRow("Longitude", data[index].longitude, " ");
                document.getElementById("data").rows["gps_altitude"].innerHTML = dataRow("gps_altitude", data[index].gps_altitude, " ");
                document.getElementById("data").rows["bmpSensor_altitude"].innerHTML = dataRow("bmpSensor_altitude", data[index].bmpSensor_altitude, " ");
                document.getElementById("data").rows["bmpSensor_pressure"].innerHTML = dataRow("bmpSensor_pressure", data[index].bmpSensor_pressure, " ");
                document.getElementById("data").rows["bmpSensor_temperature"].innerHTML = dataRow("bmpSensor_temperature", data[index].bmpSensor_temperature, " ");
                document.getElementById("data").rows["digSensor_temperature"].innerHTML = dataRow("digSensor_temperature", data[index].digSensor_temperature, " ");
                document.getElementById("data").rows["cssSensor_temperature"].innerHTML = dataRow("cssSensor_temperature", data[index].cssSensor_temperature, " ");
                document.getElementById("data").rows["cssSensor_eCO2"].innerHTML = dataRow("cssSensor_eCO2", data[index].cssSensor_eCO2, " ");
                document.getElementById("data").rows["cssSensor_TVOC"].innerHTML = dataRow("cssSensor_TVOC", data[index].cssSensor_TVOC, " ");
                document.getElementById("data").rows["UV"].innerHTML = dataRow("UV", data[index].UV, " ");
                document.getElementById("data").rows["accel_X"].innerHTML = dataRow("Accel_X", data[index].accelX, " ");
                document.getElementById("data").rows["accel_Y"].innerHTML = dataRow("Accel_Y", data[index].accelY, " ");
                document.getElementById("data").rows["accel_Z"].innerHTML = dataRow("Accel_Z", data[index].accelZ, " ");
                document.getElementById("data").rows["magnetic_X"].innerHTML = dataRow("Magnetic_X", data[index].magneticX, " ");
                document.getElementById("data").rows["magnetic_Y"].innerHTML = dataRow("Magnetic_Y", data[index].magneticY, " ");
                document.getElementById("data").rows["magnetic_Z"].innerHTML = dataRow("Magnetic_Z", data[index].magneticZ, " ");
                document.getElementById("data").rows["gyro_X"].innerHTML = dataRow("Gyro_X", data[index].gyroX, " ");
                document.getElementById("data").rows["gyro_Y"].innerHTML = dataRow("Gyro_Y", data[index].gyroY, " ");
                document.getElementById("data").rows["gyro_Z"].innerHTML = dataRow("Gyro_Z", data[index].gyroZ, " ");


                if(index < 500){
                    index = index +1;
                } else{
                    index = 0;
                }
            }
            // TODO update the real time
            document.getElementById("time").innerHTML = (theTime.getHours() < 10 ? "0" + theTime.getHours() : theTime.getHours()) + ":" + 
            (theTime.getMinutes() < 10 ? "0" + theTime.getMinutes() : theTime.getMinutes()) + ":" + 
            (theTime.getSeconds() < 10 ? "0" + theTime.getSeconds() : theTime.getSeconds());
             
            
        }

    </script>


</head>

<body>
    <table class="tableTop">
        <tr>
            <!-- tr defines a row-->
            <td>
                <!--this is where the picture and page info goes-->
                <img src="UATSpace-2.png">
            </td>
            <td>
                <h1 class="titleclass">UAT SPACE PROGRAM</h1>
            </td>
       </tr>
    </table>
    <br>
    <table id="data" border="2" width="70%" class="dataTable">
        <col style="width: 35%;">
        <col style="width: 35%;">
        <thead>
            <!--these are the table headers-->
            <th align="left">Data Type</th>
            <th align="left">Reading</th>
        </thead>
        <tbody>
            <!--this is were all the data will be displayed in a chart-->
            <tr id="seconds"></tr>
            <tr id="latitude"></tr>
            <tr id="longitude"></tr>
            <tr id="gps_altitude"></tr>
            <tr id="bmpSensor_altitude"></tr>
            <tr id="bmpSensor_pressure"></tr>
            <tr id="bmpSensor_temperature"></tr>
            <tr id="digSensor_temperature"></tr>
            <tr id="cssSensor_temperature"></tr>
            <tr id="cssSensor_eCO2"></tr>
            <tr id="cssSensor_TVOC"></tr>
            <tr id="UV"></tr>
            <tr id="accel_X"></tr>
            <tr id="accel_Y"></tr>
            <tr id="accel_Z"></tr>
            <tr id="magnetic_X"></tr>
            <tr id="magnetic_Y"></tr>
            <tr id="magnetic_Z"></tr>
            <tr id="gyro_X"></tr>
            <tr id="gyro_Y"></tr>
            <tr id="gyro_Z"> </tr>


        </tbody>

    </table>
    <br>
    The current time is: <div id = "time"></div>

    <br>
    <!--this gives a picture of the rocket launch-->
    <img src="th.jpg">
    <!--this will start the countdown timer-->
    <button id="startButton" onclick="start();" class="button">Start</button>
    <button id="stopButton" onclick="stop();" class="button" disabled=true>Stop</button>
    <br>
    <br>
    <!--This will start the sound of the rocket-->
    <button class="lgbutton" onclick="playStation()"> Play Space Station Sounds</button>
    <button class="lgbutton" onclick="playStationoff()">Turn Off Space Station Sounds</button>
    <!--this is where my countdown timer will appear-->
    <h1>COUNT DOWN TIMER</h1>
    <p id="paratag">Count Down Starts Here...</p>
    <br>
    <br>
    <button id="startButton" onclick=" countdownTimerRunn();" class="button">Start</button>
    <br>
    <script>
        var fallLaunch = new Mission(100,100,100,"Serenity","Nov",13,2021,3);
        var springLaunch = new Mission(10,10,150,"Discovery","May",8,2021,10);
        var ship1 = new SpaceCraft ("A wing Fighter", 0, 3);
        var ship2 = new SpaceCraft ("Enterprise", 0, 1004);
        
    </script>
    <br>
    <h1>Ship1 information</h1>
    <br>
    <div id= "ship1Info">Ship one info here</div>
    <br>
    <br>
    <!--<button class="lgbutton" onclick="fallLaunch.launch();">Launch Fall</button>
    <br>
    <br>
    <button class="lgbutton" onclick="springLaunch.disMissionLaunchDate();">Display Spring</button>
    <button class="lgbutton" onclick="fallLaunch. consumeFood(10);">Consume 10 Food</button>
    <br>
    <br>-->
    <!--<button class="lgbutton" onclick="alert(ship1.addAstronauts(2));">add 2 astronauts</button>-->
    <button class="lgbutton" onclick="ship1.craftInfo();">Display ship1 info</button>
    <!--<button class="lgbutton" onclick="alert('the ship now moving at ' + ship1.accelerate(10, 5) + 'm/s');">accelerate 10 m/s for 5 sec </button>-->
    
    <!--this will give ability to add astonauts and change velocity of space ship,
        Astro and velosity functions in class.js-->
    <form onsubmit="return false">
        number of Astronauts to add: <input type="number" id="formNumAstro"><br>
        <input type="submit" onclick="ship1.varAddAstro()">
    </form>
    <form onsubmit="return false">
        incresse velocity to: <input type="number" id="formIncVelocity"><br>
        for how long: <input type="number" id="formIncTime"><br>

        <input type="submit" onclick="ship1.varAccel()">
    </form>

</body>

</html>
