// Conveyor
//
//

FUNCTION_BLOCK Conveyor

    VAR_INPUT
        // SMEMA        
        xReadyToReceive: BOOL; (* Machine ready to receive next board. *)
        // environment
        xRunAllowed: BOOL; (* The machine allows you to turn on the conveyor. *)
        xBoardOnStop: BOOL; (*  *)
        udiAlarmTimer: UDINT; (*  *)
    END_VAR

    VAR_OUTPUT
        // SMEMA
        xBoardAvailable: BOOL; (* Machine has a good board ready to send (or all boards). *)
        xFailedBoardAvailable: BOOL; (* Machine has a failed board ready to send (optional). *)
        // environment
        xMotorRun: BOOL (*  *)
        xAlarm: BOOL (*  *)
    END_VAR

    VAR
        udiCounter: UDINT; (*  *)
        xConveyorFree: BOOL; (* There are no boards on the conveyor outside the sensor area. *)
        xBoardStatus: BOOL; (* Good or bad board. Good is true. *)
    END_VAR

    // Main loop
    IF xRunAllowed THEN
        
        // 
        IF NOT xConveyorFree THEN
            
            WHILE xBoardOnStop DO // TODO Add timer
                xMotorRun := true;
            END_WHILE;

            xConveyorFree := true;
            
        END_IF;

        IF xBoardOnStop THEN
            
        ELSE
            
        END_IF;
        
        
    END_IF;
    
    
END_FUNCTION_BLOCK
