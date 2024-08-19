import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;

public class AgricultureHelperSystem {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("\nWelcome to the Agriculture Helper System");
            System.out.println("Options:");
            System.out.println("1. Recommend Crops");
            System.out.println("2. Identify Plant Problems");
            System.out.println("3. Get Soil Care Tips");
            System.out.println("4. Exit Program");

            System.out.print("Select an option (1-4): ");
            int choice = scanner.nextInt();
            scanner.nextLine();  // Handle newline

            switch (choice) {
                case 1:
                    System.out.print("Enter soil type (e.g., rich, dense, loose, fertile): ");
                    String soilType = scanner.nextLine().toLowerCase();
                    System.out.println("Best crops for " + soilType + " soil: " + suggestCrops(soilType));
                    break;

                case 2:
                    System.out.print("Describe the issue (e.g., wilting leaves, curling edges, black spots, stunted growth): ");
                    String symptom = scanner.nextLine().toLowerCase();
                    System.out.println("Possible problem: " + identifyProblem(symptom));
                    break;

                case 3:
                    System.out.print("Enter your soil type (e.g., rich, dense, loose, fertile): ");
                    soilType = scanner.nextLine().toLowerCase();
                    System.out.println("Soil care tips for " + soilType + ": " + soilCareTips(soilType));
                    break;

                case 4:
                    System.out.println("Exiting the Agriculture Helper System. Thank you!");
                    scanner.close();
                    return;

                default:
                    System.out.println("Invalid option. Please try again.");
                    break;
            }
        }
    }

    private static String suggestCrops(String soilType) {
        Map<String, String[]> cropOptions = new HashMap<>();
        cropOptions.put("rich", new String[]{"Wheat", "Sugarcane", "Cotton"});
        cropOptions.put("dense", new String[]{"Rice", "Lettuce", "Broccoli"});
        cropOptions.put("loose", new String[]{"Carrot", "Peanut", "Potato"});
        cropOptions.put("fertile", new String[]{"Tomato", "Cucumber", "Onion"});

        String[] crops = cropOptions.get(soilType);
        if (crops != null) {
            return String.join(", ", crops);
        } else {
            return "No suggestions available for this soil type.";
        }
    }

    private static String identifyProblem(String symptom) {
        Map<String, String> problems = new HashMap<>();
        problems.put("wilting leaves", "Lack of Water");
        problems.put("curling edges", "Pest Infestation");
        problems.put("black spots", "Fungal Infection");
        problems.put("stunted growth", "Nutrient Deficiency");

        return problems.getOrDefault(symptom, "Problem not recognized. Consider seeking expert advice.");
    }

    private static String soilCareTips(String soilType) {
        Map<String, String> tips = new HashMap<>();
        tips.put("rich", "Add compost to enhance soil structure and fertility.");
        tips.put("dense", "Incorporate gypsum to improve soil texture and add organic matter.");
        tips.put("loose", "Apply mulch to reduce water evaporation and increase moisture retention.");
        tips.put("fertile", "Incorporate organic matter to enhance soil structure and reduce erosion.");

        return tips.getOrDefault(soilType, "No specific tips available for this soil type.");
    }
}
