# breadCalculator
A simple calculator for finding out how much stuff I need to make white bread

```
import java.util.Scanner;

public class BreadCalculator {
	
		public static void main(String[] args) {
		
		Scanner in = new Scanner(System.in);
		
		double totalWeightOfBread = 0;
		double totalPercentage = 164;
		double waterPercentage = 60;
		double saltPercentage = 2;
		double yeastPercentage = 2;
		
		System.out.println("Would you like to use a standard white dough percentage? (100% flour, 60% water, 2% salt, 2% yest) [yes/no]: ");
	
		boolean yn = (in.nextLine().toLowerCase().startsWith("y"));
		
		System.out.print("How much would you like your dough to weigh? (in grams): ");
		totalWeightOfBread = in.nextInt();
		
		if(yn) {
			breadRecipe(totalPercentage, totalWeightOfBread, waterPercentage, saltPercentage, yeastPercentage);
		} else {
			System.out.print("What percentage of water would you like? " );
			waterPercentage = in.nextDouble();
			System.out.print("What percentage of salt would you like? ");
			saltPercentage = in.nextDouble();
			System.out.print("What percentage of yeast would you like? ");
			yeastPercentage = in.nextDouble();
			
			in.close();
			
			totalPercentage = 100 + waterPercentage + saltPercentage + yeastPercentage;
			
			breadRecipe(totalPercentage, totalWeightOfBread, waterPercentage, saltPercentage, yeastPercentage);
		}
		
		
	}
	
	public static void breadRecipe(double totalPercentage, double breadWeight, double waterPercentage, double saltPercentage, double yeastPercentage) {
		
		double flourWeight = breadWeight * 100.0 / totalPercentage;
		double saltWeight = saltPercentage / 100.0 * flourWeight;
		double waterWeight = waterPercentage / 100.0 * flourWeight;
		double yeastWeight = yeastPercentage / 100.0 * flourWeight;
		
		System.out.printf("Your %.0f%% bread will use %.1fg in flour, %.1fg in salt, %.1fg in water, and %.1fg in yeast", totalPercentage, flourWeight, saltWeight, waterWeight, yeastWeight);
	}

}
```
