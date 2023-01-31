# LA1400
```
package VeljkovicSimon;
import robocode.*;

public class Goatifi extends JuniorRobot {
	public void run() {
		out.println("Get ready to rumble!");

		setColors(blue, green, brown, yellow, gray);

		while(true) {
			dance();
		}
	}
	

	public void onScannedRobot() {
		// fire hard if opponent is close because the chance is higher to hit him
		smartFire();
	//	calculatePositionX(scannedAngle, scannedDistance);
	//	calculatePositionY(scannedAngle, scannedDistance);
		double distance = scannedDistance;
		if(distance < 100){
			turnGunTo(scannedAngle);
			fire(3);
			ahead(100);
		}else{
			fire(1);
		}
	}
	//should go back because it can't be stuck in place
	public void onHitByBullet() {
		back(150);
	}
	//should go back because it can't be stuck in the wall
	public void onHitWall() {
		back(100);
	}
	//crazy movements make the robot dance
	private void dance() {
		ahead(100);
		turnLeft(150);
		turnRight(250);
		turnAheadLeft(50, 100);
		turnAheadRight(300, 150);
		turnBackLeft(25, 200);
		turnBackRight(325, 250);
	}
	//
	private void smartFire() {
		if(scannedAngle < 90){
			turnTo(scannedAngle);
			turnGunTo(scannedAngle);
			fire(1);
		}
		
		if(scannedBearing < 90){
			turnTo(scannedBearing);
			turnGunTo(scannedBearing);
			fire(1);
		}
		
		if(scannedEnergy < 30){
			turnTo(scannedAngle);
			turnGunTo(scannedAngle);
			fire(3);
		}else{
			turnTo(scannedAngle);
			turnGunTo(scannedAngle);
			fire(1);
		}
		
		if(scannedHeading < 90){
			turnTo(scannedHeading);
			turnGunTo(scannedHeading);
			fire(1);
		}
		
		if(scannedVelocity < 100){
			turnTo(scannedHeading);
			turnGunTo(scannedHeading);
			fire(1);
		}
	}
	
/*	public double calculatePositionX(int angle, int distance); {
		double x =  Math.sin(angle) * distance;
		return robotX + x;
	}
	
	public double calculatePositionY(int angle, int distance); {
		double y =  Math.cos(angle) * distance;
		return robotY + y;
	} */

}
```
