## Flowchart:
https://drive.google.com/file/d/1DJzACQig92aDVebRjU9ay4Vre9uvereI/view?usp=sharing
https://drive.google.com/file/d/15flsUxNClAEv9g9Vak60zdVLT6AaWT9C/view?usp=sharing

## Challenges:
I had some floating-point rounding issues, so I just needed to change the numbers in the formatting.

## Video:
https://www.loom.com/share/9efd219cf9694f728bda7cdd9c20aa19

## Code:
    import javax.swing.*;
    import java.awt.*;
    import java.awt.event.ActionEvent;
    import java.awt.event.ActionListener;
    
    public class SalaryCalculator {
        public static void main(String[] args) {
            // Create the main window (JFrame)
            JFrame frame = new JFrame("Yearly Salary Calculator");
            frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
            frame.setSize(350, 200);
            frame.setLayout(new GridLayout(4, 2, 10, 10)); // rows, cols, hgap, vgap
    
            // Create labels
            JLabel wageLabel = new JLabel("Hourly wage ($):");
            JLabel hoursLabel = new JLabel("Hours per week:");
            JLabel resultLabel = new JLabel("Yearly salary: ");
            JLabel outputLabel = new JLabel("");  // empty label to display result
    
            // Create text fields for input
            JTextField wageField = new JTextField();
            JTextField hoursField = new JTextField();
    
            // Create button to calculate salary
            JButton calcButton = new JButton("Calculate");
    
            // Add ActionListener to the button
            calcButton.addActionListener(new ActionListener() {
                @Override
                public void actionPerformed(ActionEvent e) {
                    try {
                        // Parse user inputs
                        double hourlyWage = Double.parseDouble(wageField.getText());
                        double hoursPerWeek = Double.parseDouble(hoursField.getText());
    
                        // Calculate yearly salary (assuming 52 weeks/year)
                        double yearlySalary = hourlyWage * hoursPerWeek * 52;
    
                        // Display formatted salary
                        outputLabel.setText(String.format("$%.2f", yearlySalary));
                    } catch (NumberFormatException ex) {
                        // Handle invalid input
                        outputLabel.setText("Please enter valid numbers!");
                    }
                }
            });
    
            // Add components to frame
            frame.add(wageLabel);
            frame.add(wageField);
            frame.add(hoursLabel);
            frame.add(hoursField);
            frame.add(resultLabel);
            frame.add(outputLabel);
            frame.add(new JLabel(""));  // empty cell for layout balance
            frame.add(calcButton);
    
            // Make frame visible
            frame.setVisible(true);
        }
    }
