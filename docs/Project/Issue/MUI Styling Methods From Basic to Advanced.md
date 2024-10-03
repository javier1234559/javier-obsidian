---
Created: 14:23 29-09-2024
tags:
  - issue
---
>Hint 💡 
>- Use 




1. Using Built-in Component Props
   - Description: Utilize pre-defined props to style components.
   - Example:
     ```jsx
     <Button variant="contained" color="primary" size="large">
       Styled Button
     </Button>
     ```

2. Applying CSS Classes
   - Description: Use MUI's `className` prop to apply custom CSS classes.
   - Example:
     ```jsx
     import { makeStyles } from '@mui/styles';

     const useStyles = makeStyles({
       customButton: {
         background: 'linear-gradient(45deg, #FE6B8B 30%, #FF8E53 90%)',
         border: 0,
         borderRadius: 3,
         boxShadow: '0 3px 5px 2px rgba(255, 105, 135, .3)',
         color: 'white',
         height: 48,
         padding: '0 30px',
       },
     });

     function CustomButton() {
       const classes = useStyles();
       return <Button className={classes.customButton}>Custom Styled Button</Button>;
     }
     ```

3. Inline Styling with the `sx` Prop
   - Description: Use the `sx` prop for one-off custom styling.
   - Example:
     ```jsx
     <Box
       sx={{
         width: 300,
         height: 300,
         backgroundColor: 'primary.dark',
         '&:hover': {
           backgroundColor: 'primary.main',
           opacity: [0.9, 0.8, 0.7],
         },
       }}
     />
     ```

4. Creating Custom Themes
   - Description: Customize the default MUI theme for consistent styling.
   - Example:
     ```jsx
     import { createTheme, ThemeProvider } from '@mui/material/styles';

     const theme = createTheme({
       palette: {
         primary: {
           main: '#1976d2',
         },
         secondary: {
           main: '#dc004e',
         },
       },
       typography: {
         fontFamily: 'Roboto, Arial, sans-serif',
         h1: {
           fontSize: '2.5rem',
           fontWeight: 500,
         },
       },
     });

     function App() {
       return (
         <ThemeProvider theme={theme}>
           {/* Your app components */}
         </ThemeProvider>
       );
     }
     ```

5. Using Styled Components
   - Description: Create custom styled components using MUI's styled API.
   - Example:
     ```jsx
     import { styled } from '@mui/material/styles';
     import Button from '@mui/material/Button';

     const CustomButton = styled(Button)(({ theme }) => ({
       color: theme.palette.getContrastText(theme.palette.secondary.main),
       backgroundColor: theme.palette.secondary.main,
       '&:hover': {
         backgroundColor: theme.palette.secondary.dark,
       },
       padding: theme.spacing(2),
     }));

     function MyComponent() {
       return <CustomButton>Custom Styled Button</CustomButton>;
     }
     ```

6. Overriding Component Styles
   - Description: Override default styles of MUI components.
   - Example:
     ```jsx
     import { createTheme, ThemeProvider } from '@mui/material/styles';

     const theme = createTheme({
       components: {
         MuiButton: {
           styleOverrides: {
             root: {
               fontSize: '1rem',
               textTransform: 'none',
             },
             contained: {
               boxShadow: 'none',
               '&:hover': {
                 boxShadow: 'none',
               },
             },
           },
         },
       },
     });

     function App() {
       return (
         <ThemeProvider theme={theme}>
           <Button variant="contained">Custom Default Button</Button>
         </ThemeProvider>
       );
     }
     ```

7. Responsive Styling Techniques
   - Description: Apply responsive styles using MUI's breakpoints.
   - Example:
     ```jsx
     import { useTheme } from '@mui/material/styles';
     import useMediaQuery from '@mui/material/useMediaQuery';

     function ResponsiveComponent() {
       const theme = useTheme();
       const isSmallScreen = useMediaQuery(theme.breakpoints.down('sm'));

       return (
         <Box
           sx={{
             width: {
               xs: '100%', // 0+
               sm: '50%',  // 600+
               md: '33%',  // 900+
             },
             bgcolor: isSmallScreen ? 'primary.main' : 'secondary.main',
           }}
         >
           Responsive Box
         </Box>
       );
     }
     ```

8. Dynamic Styling with React Hooks
   - Description: Use React hooks to apply dynamic styles.
   - Example:
     ```jsx
     import { useState } from 'react';
     import { Button, Box } from '@mui/material';

     function DynamicStyleComponent() {
       const [isHovered, setIsHovered] = useState(false);

       return (
         <Box
           sx={{
             bgcolor: isHovered ? 'primary.main' : 'secondary.main',
             transition: 'background-color 0.3s',
             p: 2,
           }}
           onMouseEnter={() => setIsHovered(true)}
           onMouseLeave={() => setIsHovered(false)}
         >
           Hover me!
         </Box>
       );
     }
     ```

9. Creating and Using Custom Components
   - Description: Build reusable custom components with consistent styling.
   - Example:
     ```jsx
     import { forwardRef } from 'react';
     import { Button, styled } from '@mui/material';

     const StyledButton = styled(Button)(({ theme }) => ({
       borderRadius: theme.shape.borderRadius * 2,
       textTransform: 'none',
     }));

     const CustomButton = forwardRef((props, ref) => (
       <StyledButton ref={ref} variant="contained" color="primary" {...props} />
     ));

     function App() {
       return <CustomButton>My Custom Button</CustomButton>;
     }
     ```

10. Advanced Theme Customization
    - Description: Create complex themes with nested customizations.
    - Example:
     ```jsx
     import { createTheme, ThemeProvider } from '@mui/material/styles';

     const theme = createTheme({
       palette: {
         mode: 'light',
         primary: {
           main: '#1976d2',
           light: '#42a5f5',
           dark: '#1565c0',
           contrastText: '#ffffff',
         },
       },
       typography: {
         fontFamily: '"Roboto", "Helvetica", "Arial", sans-serif',
         h1: {
           fontSize: '2.5rem',
           fontWeight: 500,
           lineHeight: 1.2,
         },
       },
       shape: {
         borderRadius: 8,
       },
       components: {
         MuiButton: {
           styleOverrides: {
             root: {
               textTransform: 'none',
             },
           },
           variants: [
             {
               props: { variant: 'dashed' },
               style: {
                 border: `2px dashed ${theme.palette.primary.main}`,
                 color: theme.palette.primary.main,
               },
             },
           ],
         },
       },
     });

     function App() {
       return (
         <ThemeProvider theme={theme}>
           <Button variant="dashed">Custom Variant Button</Button>
         </ThemeProvider>
       );
     }
     ```