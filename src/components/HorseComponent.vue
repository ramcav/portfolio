<template>
    <div id="ascii-container">
      <pre :style="currentColorStyle">{{ currentFrame }}</pre>
    </div>
  </template>
  
  <script>
  export default {
    name: "AsciiHorse",
    data() {
      return {
        frames: [
          `                                                                  
                                                      ##              
                                                     #######          
                                                   ###########        
                                                   #############      
                                                 #################    
                       ########                 #########  #######    
                   ######################################      ##     
             ###########################################              
           #####  ######################################              
         #####    #####################################               
         #####     ###################################                
                     ################################                 
                ##############  #####################                 
                 ###########         ###############                  
                  ########                ######                      
                   ######                #######                      
                    ##  ###             #### ####                     
                   ###    ###        ######   ###                     
                  ###      ##         ###########                     
                           ##       ###                               
                                   ###                                
                                   ##                                 
                                  ##                                  
            `,
          `                                           
                                                    ###               
                                                 ########             
                                             ##############           
                                           #################          
                                           ###################        
                     #########       ################   #######       
      ########   ###################################       ##         
       ############################################                   
          #     ###################################                   
                ###################################                   
                ##################################                    
                 #################################                    
                  ############   ####################                 
                  #####   ####                    ######              
                 #####     ####                   ##   ##             
               #####       #####             ######     ###           
                ###           ####                       ##           
                ###             ####                     ###          
                 ###                ###                               
                  ###                                                 
                     ###                                              
            `,
          `                                            
                                                    ######            
                                                ###########           
                                             ################         
                                           ###################        
                                        #######################       
      ###           #################################     ######      
      ##############################################        ##        
          ##     ###################################                  
                ###################################                   
                ###################################                   
                #######################################               
                ############   ##################### ###              
               ####### #####                   #####  ##              
             ######     ####                     ######               
            ####        ###                        ####               
            ##          ####                       ## ###             
           ##            ###                            #####         
           ##              ##                              ###        
           ###              ####                                      
             ###               ###                                    
            `,
          `                                           
                                                        ####          
                                                    #########         
                                                 #############        
                                                ################      
                                             ####################     
                                        #################  ######     
       ################################################       ###     
       ######### #####################################                
          ##    ######################################                
               #######################################                
               #######################################                
               ############################################           
              #############       #################   ######          
            ######  #####                      #####      ##          
           #####   #####                         ###      ###         
          ###    #####                            ###     ###         
        ###       ###                              ###    ###         
       ###        ###                               ##     #          
      ###          ###                               ##               
     ###            #####                            ####             
      ##               ###                             ###            
            `
        ],
        currentFrameIndex: 0,
        grayLevel: 50,
        increasing: true,
        fontSize: 24
      };
    },
    computed: {
    currentFrame() {
      return this.frames[this.currentFrameIndex];
    },
    currentColorStyle() {
      return {
        color: `rgb(${this.grayLevel}, ${this.grayLevel}, ${this.grayLevel})`,
        fontSize: `${this.fontSize}px`, // Adjust font size dynamically
      };
    },
  },
  mounted() {
    this.startAnimation();
    this.startColorAnimation();
    this.updateFontSize(); // Set initial font size
    window.addEventListener("resize", this.updateFontSize); // Adjust size on window resize
  },
  beforeUnmount() {
    window.removeEventListener("resize", this.updateFontSize); // Clean up the event listener
  },
  methods: {
    startAnimation() {
      setInterval(() => {
        this.currentFrameIndex =
          (this.currentFrameIndex + 1) % this.frames.length;
      }, 130); // Adjust interval for speed
    },
    startColorAnimation() {
      setInterval(() => {
        if (this.increasing) {
          this.grayLevel += 5;
          if (this.grayLevel >= 200) this.increasing = false;
        } else {
          this.grayLevel -= 5;
          if (this.grayLevel <= 0) this.increasing = true;
        }
      }, 50); // Adjust speed of color gradient change
    },
    updateFontSize() {
      const screenWidth = window.innerWidth;
      // Adjust the font size based on the screen width
      if (screenWidth > 1200) {
        this.fontSize = 24; // Large screens
      } else if (screenWidth > 768) {
        this.fontSize = 18; // Medium screens
      } else {
        this.fontSize = 16; // Small screens
      }
    },
  },
};
</script>

<style scoped>
#ascii-container {
  font-family: monospace;
  white-space: pre;
  overflow: hidden;
  text-align: center;
  padding: 20px;
}
</style>