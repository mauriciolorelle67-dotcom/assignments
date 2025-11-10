## Flowchart:
https://drive.google.com/file/d/10m2-6MAokkRZMmEdT2JocEZywut1JbHL/view?usp=sharing

## Challenges:
I was a little tired so I was having some trouble with the event logic. 

## Video:
https://www.loom.com/share/fc3fc8c2b09b4c44a7166f0d4642efa0

## Code:
    import javax.swing.*;
    import java.awt.*;
    import java.awt.event.*;
    
    public class MilesToKmConverter {
        public static void main(String[] args) {
            // Create main window
            JFrame frame = new JFrame("Miles to Kilometers Converter");
            frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
            frame.setSize(300, 150);
            frame.setLayout(new GridLayout(3, 2, 10, 10));
    
            // Label for miles
            JLabel milesLabel = new JLabel("Enter distance (miles):");
    
            // Spinner for user input (allows numeric adjustment)
            SpinnerNumberModel model = new SpinnerNumberModel(0.0, 0.0, 10000.0, 0.1);
            JSpinner milesSpinner = new JSpinner(model);
    
            // Label for result
            JLabel resultLabel = new JLabel("Distance in kilometers:");
            JLabel outputLabel = new JLabel(""); // where result is displayed
    
            // Button to perform conversion
            JButton convertButton = new JButton("Convert");
    
            // ActionListener for the button
            convertButton.addActionListener(new ActionListener() {
                @Override
                public void actionPerformed(ActionEvent e) {
                    // Get the spinner value
                    double miles = (Double) milesSpinner.getValue();
    
                    // Convert miles to kilometers (1 mile = 1.60934 km)
                    double kilometers = miles * 1.60934;
    
                    // Display result
                    outputLabel.setText(String.format("%.3f km", kilometers));
                }
            });
    
            // Add components to frame
            frame.add(milesLabel);
            frame.add(milesSpinner);
            frame.add(resultLabel);
            frame.add(outputLabel);
            frame.add(new JLabel("")); // spacer
            frame.add(convertButton);
    
            // Display window
            frame.setVisible(true);
        }
    }
