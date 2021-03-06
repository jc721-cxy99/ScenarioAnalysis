Considering Carbon
Many people choose to buy an electric car, not because of cost but out of concern for the environment. This is a benefit that is difficult to fully capture, but certain things like greenhouse gas emissions can be measured.

Greenhouse gases (GHGs) trap heat in the Earth’s atmosphere and are believed to contribute to global climate change. Carbon dioxide (CO2) is the main GHG produced by human activity, and the two major human activities responsible for CO2 emission are electric power generation and combustion of fossil fuels for transportation. You can read a little more about CO2 emission on the EPA website.

According to the EPA, there are 8.887 kg of CO2 released with the combustion of each gallon of gasoline. This is the amount of CO2 coming out the tailpipe of a gas powered vehicle.

This means that we can estimate the total CO2 emitted over the three-year lease of a vehicle. Assuming the vehicle consumes 1 gallon of gas for every 34 miles and that the lease allowance milage is 12,000 miles per year, we can compute the number of gallons of gasoline needed to drive an estimated 36,000 miles and multiplying by 8.887kg/gal as follows:

36,000mi/(34 mi/gal) x 8.887 kg/gal = 1,058.82 gal x 8.887kg/gal = 9,409.76kg.

To drive 36,000 miles, the vehicle uses 1,058.82 gallons of gasoline and produces 9,409.76 kg of CO2.

You can do this same calculation for any gas-powered car by plugging in the number of miles driven (M) and the fuel efficiency of the vehicle in miles per gallon (N).
Total kg of CO2 emitted = [M miles/ (N (miles/gallon))] * 8.887 (kg CO2 / gallon)  (Equation1)

To figure out how much CO2 is emitted in generating the electricity to charge the battery of an electricity-powered car over a three-year lease, let’s begin by estimating the total energy for battery charging needed to drive 36,000 miles. Assuming that it takes 60kWh to fully charge the car and that the car can drive for 238 miles per charge we estimate the total energy needed for battery charging needed to drive 36,000 miles is:

36,000 mi/(238 mi/charge) x 60 kWh/charge = 9,075.6 kWh.

According to the EPA’s Power Profiler website, 998.4 pounds of CO2 are emitted per mWh on average across the United States.

Converting units, there are about .45kg per pound, resulting in the following total CO2 emission in kg to power the car:

9,075.6 kWh * [ 998.4 lbs CO2/ MWh * 1MWh/1000Kwh * 0.45kg/lb ] = 4077.5 kg/CO2

Given all of this, we now have the capability to estimate the CO2 emission resulting from driving an electric vehicle. It boils down to plugging in the number of miles driven (M), battery storage capacity (E), and the driving range on a charge (R) into the following equation.


This equation looks hairy, but we can deconstruct it by noticing that the quantity in brackets on the left is electricity consumption, and the quantity in brackets on the right is essentially just unit conversions to get us from kWh of electricity to kg of CO2.

Given Equation 2 and Equation 1 from the previous section, we can figure out the CO2 emissions from any gas-powered car and any electric car, and that’s what we will do now.

Lease stores information about the a vehicle’s lease.  The amount due at signing, the number of months for the lease, monthly cost and the number of miles per year.
Fuel stores information related to the type of fuel the vehicle operates with. For electric-powered vehicles it includes the amount of kWh it takes to charge the battery in addition to the amount of miles/charge or miles/gals for gas-powered vehicles.
Vehicle includes fuel and lease information in addition to CO2 emitted during the lease length, other costs (oil change or home charger), fuel cost and finally the total cost to have the vehicle for the lease length.
ScenarioAnalysis allows us to compare several vehicles given the current gas and electricity prices. The class reads the text file vehicles.txt which contains vehicle data. You can update this file to add new vehicles.
[ M miles/ (R (miles/charge))*  (R KWh) / charge]* [(998.4 lbs CO2/ MWh) * 1 MW/ 1000 KWh * 0.45kg / lb] =kg of CO2   (Equation2)





 public void computeCO2EmissionsAndCost () {}
This method computes the CO2 emissions, fuel, lease and total cost for every vehicle in the vehicles array.

Use the main method provided in the ScenarioAnalysis class to test your method.

This assignment can used to compare among several car options a buyer is considering.

Update the vehicles.txt file according to lease information, fuel, etc. The file has either gas or electric powered vehicles. The format is as follow:

[gas	name]	[cash due at lease signing]	[lease length in months]	[monthly lease cost]	[mileage allowance per 12 months]	[miles per gallon]	[cost of oil change]
[electric	name]	[cash due at signing lease]	[lease length in months]	[monthly lease cost]	[mileage allowance per 12 months]	[miles per kWh/charge]	[kWh per charge]	[cost of home charger]





public class ScenarioAnalysis {

    // Instance variables
    private Vehicle[] vehicles;       // all vehicless being analyzed 
    private double  gasPrice;         // price of one gallon of gas in dollars
    private double  electricityPrice; // price of 1 kWh in cents of a dollar, c$/kWh

public ScenarioAnalysis ( double gasPrice, double electricityPrice ) {
        this.gasPrice = gasPrice;
        this.electricityPrice = electricityPrice;
    }

    /*
     * Updates the price of gas
     * Call computeCO2EmissionsAndCost() whenever there is an update on gas prices
     */
public void setGasPrice ( double gasPrice ) {
        this.gasPrice = gasPrice;
        computeCO2EmissionsAndCost();
    }

    /*
     * Returns the gas price
     */ 
public double getGasPrice () {
        return gasPrice;
    }

    /*
     * Updates the price of electricity
     * Call computeCO2EmissionsAndCost() whenever there is an update on electricity prices
     */
public void setElectricityPrice ( double electricityPrice ) {
        this.electricityPrice = electricityPrice;
    }
    
    /*
     * Returns electricity price
     */
public double getElectricityPrice () {
        return electricityPrice;
    }

    /*
     * Computes and updates the CO2 emissions, fuel cost and total cost for each 
     * vehicle in the vehicles array.
     */
public void computeCO2EmissionsAndCost () {
     /*
      * write your code here
      *
      */
    }

    /*
     * Returns vehicles array
     */
public Vehicle[] getVehicles () {
        return vehicles;
    }

    /*
     * Prints all vehicles
     */
public void printVehicles () {
        for ( Vehicle v : vehicles ) {
            StdOut.println(v);
        }
    }

    /*
     * Populates the array vehicles from file vehicles.txt
     * 
     * File Format: The file can have either gas or electric lines
     * 
     * gas,      name, cash due at signing lease,lease length in months, monthly lease cost, mileage allowance per 12 months, miles per gallon, cost of oil change
     * electric, name, cash due at signing lease,lease length in months, monthly lease cost, mileage allowance per 12 months, miles per kWh/charge, kWh per charge, cost of home charger
     */ 
public void populateVehicleArray () {
        StdIn.setFile("vehicles.txt");

        // read the number of car models and allocate array
int numberOfCars = StdIn.readInt();
        vehicles = new Vehicle[numberOfCars];

   for (int i = 0; i < numberOfCars; i++) {
            String fuelType = StdIn.readString();
            String name     = StdIn.readString();

            // Lease information
  double dueAtSigning  = StdIn.readDouble();
            int numberOfMonths = StdIn.readInt();
            double montlyCost  = StdIn.readDouble();
            int mileageAllowance = StdIn.readInt();
            Lease lease = new Lease(dueAtSigning,numberOfMonths,montlyCost,mileageAllowance);

            // Fuel
  double usage = StdIn.readDouble();
            Fuel fuel = null; 
            if ( fuelType.toLowerCase().equals("electric")) {
                double kWhPerCharge = StdIn.readDouble();
                fuel = new Fuel (usage, kWhPerCharge);
            } else {
                fuel = new Fuel (usage);
            }

            // other cost include oil change for gas-powered or home charger for eletric-powered
            double otherCost = StdIn.readDouble();

            // Instatiate the new vehicle
  vehicles[i] = new Vehicle (name, fuel, lease, otherCost);
        }
    }

    /*
     * Test client
     */
 public static void main (String[] args) {
        ScenarioAnalysis sa = new ScenarioAnalysis(3.45, 0.3);
        sa.populateVehicleArray();
        sa.setGasPrice(2.23);           // $2.23 per gallon of gas
        sa.setElectricityPrice(16.14);  // c$16.14 per kWh
        sa.computeCO2EmissionsAndCost();
        sa.printVehicles();
    }
}
