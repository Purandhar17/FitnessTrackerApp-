# FitnessTrackerApp
Whether you're a seasoned athlete or just starting your fitness journey, our app provides the tools you need to succeed.
//code for fitnesstrackerapp in java
import java.util.ArrayList;
import java.util.List;

public class FitnessTrackerApp {
    public static void main(String[] args) {
        FitnessTrackerApp app = new FitnessTrackerApp();
        User user = new User("John Doe", 25, 75.0, 1.8);
 app.addUser(user);
        app.logWorkout(user, new Workout("Running", 30, 300));
        app.logWorkout(user, new Workout("Cycling", 45, 400));
        app.setGoal(user, new Goal("Lose 5 kg", "Weight Loss"));
   app.showUserStats(user);
    }
 private List<User> users;
public FitnessTrackerApp() {
        this.users = new ArrayList<>();
    }
 public void addUser(User user) {
        users.add(user);
    }
 public void logWorkout(User user, Workout workout) {
        user.addWorkout(workout);
    }
public void setGoal(User user, Goal goal) {
        user.setGoal(goal);
    }
public void showUserStats(User user) {
        System.out.println("User: " + user.getName());
        System.out.println("Age: " + user.getAge());
        System.out.println("Weight: " + user.getWeight());
        System.out.println("Height: " + user.getHeight());
        System.out.println("Total Calories Burned: " + user.getTotalCaloriesBurned());
        System.out.println("Current Goal: " + user.getGoal().getDescription());
    }
 // User class
    static class User {
        private String name;
        private int age;
        private double weight;
        private double height;
        private List<Workout> workouts;
        private Goal goal;
 public User(String name, int age, double weight, double height) {
            this.name = name;
            this.age = age;
            this.weight = weight;
            this.height = height;
            this.workouts = new ArrayList<>();
        }
 public String getName() {
            return name;
        }
public int getAge() {
            return age;
        }public double getWeight() {
            return weight;
        }
public double getHeight() {
            return height;
        }
 public void addWorkout(Workout workout) {
            workouts.add(workout);
        }
public double getTotalCaloriesBurned() {
            return workouts.stream().mapToDouble(Workout::getCaloriesBurned).sum();
        }

public void setGoal(Goal goal) {
            this.goal = goal;
        }
public Goal getGoal() {
            return goal;
        }
    }
  // Workout class
    static class Workout {
        private String type;
        private int duration; // in minutes
        private double caloriesBurned;
public Workout(String type, int duration, double caloriesBurned) {
            this.type = type;
            this.duration = duration;
            this.caloriesBurned = caloriesBurned;
        }
public String getType() {
            return type;
        }
public int getDuration() {
            return duration;
        }
public double getCaloriesBurned() {
            return caloriesBurned;
        }
    }
  // Goal class
    static class Goal {
        private String description;
        private String category;
 public Goal(String description, String category) {
            this.description = description;
            this.category = category;
        }

public String getDescription() {
            return description;
        }
public String getCategory() {
            return category;
        }
    }
}
