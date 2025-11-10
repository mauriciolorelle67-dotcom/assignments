## Flowchart:
https://drive.google.com/file/d/10J-9elz0_wn1nVnOOI5CysjtYZ6hN0FL/view?usp=sharing
https://drive.google.com/file/d/1usXZyS5cE3q92DXo4HSUNSj8mPDMnhM0/view?usp=sharing

## Challenges:
I had some trouble formatting the GridLayout neatly.

## Video:
https://www.loom.com/share/702c667f49e0451dba0664fe40604686

## Code:
    import javax.swing.*;
    import java.awt.*;
    import java.awt.event.*;
    import java.text.NumberFormat;
    
    public class DistanceConverter {
        public static void main(String[] args) {
            // Create frame
            JFrame frame = new JFrame("Distance Converter");
            frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
            frame.setSize(350, 220);
            frame.setLayout(new GridLayout(5, 2, 10, 10));
    
            // Label and formatted text field for user input
            JLabel milesLabel = new JLabel("Enter distance (miles):");
            NumberFormat numberFormat = NumberFormat.getNumberInstance();
            JFormattedTextField milesField = new JFormattedTextField(numberFormat);
            milesField.setValue(0.0);
    
            // Labels for results
            JLabel kmLabel = new JLabel("Kilometers:");
            JLabel mLabel = new JLabel("Meters:");
            JLabel ftLabel = new JLabel("Feet:");
    
            JLabel kmResult = new JLabel("");
            JLabel mResult = new JLabel("");
            JLabel ftResult = new JLabel("");
    
            // Button to trigger calculation
            JButton calcButton = new JButton("Convert");
    
            // Add ActionListener for the button
            calcButton.addActionListener(new ActionListener() {
                @Override
                public void actionPerformed(ActionEvent e) {
                    try {
                        // Get user input from formatted field
                        double miles = ((Number) milesField.getValue()).doubleValue();
    
                        // Convert to other units
                        double kilometers = miles * 1.60934;
                        double meters = kilometers * 1000;
                        double feet = miles * 5280;
    
                        // Display results
                        kmResult.setText(String.format("%.3f km", kilometers));
                        mResult.setText(String.format("%.2f m", meters));
                        ftResult.setText(String.format("%.2f ft", feet));
                    } catch (Exception ex) {
                        kmResult.setText("Invalid input");
                        mResult.setText("");
                        ftResult.setText("");
                    }
                }
            });
    
            // Add components to frame
            frame.add(milesLabel);
            frame.add(milesField);
            frame.add(kmLabel);
            frame.add(kmResult);
            frame.add(mLabel);
            frame.add(mResult);
            frame.add(ftLabel);
            frame.add(ftResult);
            frame.add(new JLabel("")); // spacing cell
            frame.add(calcButton);
    
            // Show frame
            frame.setVisible(true);
        }
    }
