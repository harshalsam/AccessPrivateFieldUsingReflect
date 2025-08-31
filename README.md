# AccessPrivateFieldUsingReflect
This project demonstrates how to use Java Reflection API to access and manipulate private fields of a class at runtime. Normally, private fields are encapsulated and cannot be accessed directly outside their class. However, with reflection, developers can bypass normal access control for purposes like testing, debugging, or working with legacy code
//Program: Reflect Private Field and Modify it
import java.lang.reflect.Field;

class Student {
 private String name = "Harshal";  // private field
}

public class ReflectPrivateField {
 public static void main(String[] args) {
	 System.out.println("NAME:HARSHAL SAM A");
	 System.out.println("REG:2117240070112");
	 
     try {
         // Step 1: Create object
         Student obj = new Student();

         // Step 2: Get the Class object
         Class<?> cls = obj.getClass();

         // Step 3: Get the private field 'name'
         Field field = cls.getDeclaredField("name");

         // Step 4: Make it accessible
         field.setAccessible(true);

         // Step 5: Get current value
         String oldValue = (String) field.get(obj);
         System.out.println("Before Modification: " + oldValue);

         // Step 6: Modify private field
         field.set(obj, "Sam");

         // Step 7: Get new value
         String newValue = (String) field.get(obj);
         System.out.println("After Modification: " + newValue);

     } catch (Exception e) {
         e.printStackTrace();
     }
 }
}
