import java.util.ArrayList;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        RentalAgency rentalAgency = new RentalAgency();

        // Adding cars
        rentalAgency.addCar(new Car("001", "Toyota", "Corolla"));
        rentalAgency.addCar(new Car("002", "Honda", "Civic"));

        // Adding customers
        rentalAgency.addCustomer(new Customer("1001", "John Doe", "john@example.com"));
        rentalAgency.addCustomer(new Customer("1002", "Jane Smith", "jane@example.com"));

        // Renting a car
        rentalAgency.rentCar("001", "1001");

        // Displaying all entities
        rentalAgency.displayEntities();
    }
}

class Car {
    private String carId;
    private String make;
    private String model;
    private boolean available;

    // Constructor
    public Car(String carId, String make, String model) {
        this.carId = carId;
        this.make = make;
        this.model = model;
        this.available = true; // Initially available
    }

    // Getters and setters
    public String getCarId() {
        return carId;
    }

    public String getMake() {
        return make;
    }

    public String getModel() {
        return model;
    }

    public boolean isAvailable() {
        return available;
    }

    public void setAvailable(boolean available) {
        this.available = available;
    }

    public String toString() {
        return "Car ID: " + carId + ", Make: " + make + ", Model: " + model + ", Available: " + available;
    }
}

class Customer {
    private String customerId;
    private String name;
    private String email;

    // Constructor
    public Customer(String customerId, String name, String email) {
        this.customerId = customerId;
        this.name = name;
        this.email = email;
    }

    // Getters and setters
    public String getCustomerId() {
        return customerId;
    }

    public String getName() {
        return name;
    }

    public String getEmail() {
        return email;
    }

    public String toString() {
        return "Customer ID: " + customerId + ", Name: " + name + ", Email: " + email;
    }
}

class RentalAgency {
    private List<Car> cars;
    private List<Customer> customers;

    // Constructor
    public RentalAgency() {
        cars = new ArrayList<>();
        customers = new ArrayList<>();
    }

    // Method to add a car to the agency
    public void addCar(Car car) {
        cars.add(car);
    }

    // Method to add a customer to the agency
    public void addCustomer(Customer customer) {
        customers.add(customer);
    }

    // Method to rent a car to a customer
    public void rentCar(String carId, String customerId) {
        Car car = findCarById(carId);
        if (car != null && car.isAvailable()) {
            car.setAvailable(false);
            // Additional logic for rental transaction
        } else {
            System.out.println("Car not available for rent.");
        }
    }

    // Method to display entities
    public void displayEntities() {
        System.out.println("Cars:");
        for (Car car : cars) {
            System.out.println(car);
        }

        System.out.println("\nCustomers:");
        for (Customer customer : customers) {
            System.out.println(customer);
        }
    }

    // Helper method to find a car by ID
    private Car findCarById(String carId) {
        for (Car car : cars) {
            if (car.getCarId().equals(carId)) {
                return car;
            }
        }
        return null;
    }
}
