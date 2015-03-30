# Practice
public Move move() {
        // if direction is not yet set, choose a random one
        if (direction == null) {
            direction = new Move(rand.nextFloat() * 2.0 - 1.0, rand.nextFloat() * 2.0 - 1.0);
            // scale direction to lenght and quantize it to maximize distance covered.
            direction = direction.scaledToLength(getMaxAllowedDistance()).quantized();
        }
        GameLocation myLocation = this.getLocation();
        ArrayList<GameLocation> PastureLocations = board.getPasturePositions();
        int i = 0;
        GameLocation nearestPasture = PastureLocations.get(0);
        
        int x = 0;
        int y = 0;
       
        
        
        ArrayList<GameLocation> trk = new ArrayList();
            trk.add(getLocation());
            //trk.add(new GameLocation(0,0));  
            trk.add(nearestPasture);
            removeVisualizations(); // remove all previously set tracks
            visualizeTrack(trk);
            
            
            
            
        
            
       if(myLocation.x - nearestPasture.x  < 0){ //switch signs back
            x=1;
            //direction.delta_x = 1;
        }
       else if(myLocation.x - nearestPasture.x  > 0){
           x = -1;
            //direction.delta_x = -1;   
        }
        else
        {
            x = 0;
           //direction.delta_x = 0;
        }
        if(myLocation.y - nearestPasture.y   < 0){
         y= 1;
            //direction.delta_y = 1;
        }
        else if(myLocation.y - nearestPasture.y   > 0){
            y = -1;
            //direction.delta_y = -1;
        }
        else{
          y = 0;
            //direction.delta_y = 0;
        }
         
         return new Move(x,y);
