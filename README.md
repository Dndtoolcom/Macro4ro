# Macro4ro

 begin
     Color.Limit area of interest to window("Ragnarok", "yes")
     Window.Set location("Ragnarok", "yes", "0", "0")
     // Variables Declared
     Variable.Set("a", "0")
     Variable.Set("b", "0")
     Variable.Set("c", "0")
     Variable.Set("d", "0")
     Variable.Set("e", "0")
     Variable.Set("f", "0")
     Variable.Set("h", "0")
     Variable.Set("i", "0")
     Variable.Copy("a1", "a")
     Variable.Copy("b1", "b")
     Variable.Copy("c1", "c")
     Variable.Copy("d1", "d")
     Variable.Copy("e1", "e")
     Variable.Copy("f1", "f")
     Variable.Copy("h1", "h")
     Variable.Copy("i1", "i")
     Variable.Set("l", "0")
     Variable.Set("at", "0")
     Variable.Set("1", "1")
     Variable.Add to collection("and", "1")
     Variable.Set("2", "2")
     Variable.Add to collection("and", "2")
     Variable.Set("3", "3")
     Variable.Add to collection("and", "3")
     Variable.Set("4", "4")
     Variable.Add to collection("and", "4")
     Variable.Set("5", "5")
     Variable.Add to collection("and", "5")
     Variable.Set("6", "6")
     Variable.Add to collection("and", "6")
     Variable.Set("7", "7")
     Variable.Add to collection("and", "7")
     Variable.Set("8", "8")
     Variable.Add to collection("and", "8")
     Variable.Set("j", " ")
     Variable.Set random number("g", "1", "8")
     Variable.Get from collection("and", "{g}", "j")
     Variable.Set("mx", "651")
     Variable.Set("my", "90")
     Variable.Set("mx2", "518")
     Variable.Set("my2", "504")
     Variable.Set("mx3", "353")
     Variable.Set("my3", "391")
     Variable.Set("mx4", "827")
     Variable.Set("my4", "252")
     Variable.Set("mx5", "399")
     Variable.Set("my5", "248")
     Variable.Set("mx6", "861")
     Variable.Set("my6", "385")
     Variable.Set("mx7", "641")
     Variable.Set("my7", "599")
     Variable.Set("mx8", "839")
     Variable.Set("my8", "519")
     Function.Execute("AutoPots")
     Function.Execute("{j}")
     Variable.Set random number("g", "1", "8")
     Variable.Get from collection("and", "{g}", "j")
     Function.Execute("{j}")
     Variable.Set random number("g", "1", "8")
     Variable.Get from collection("and", "{g}", "j")
     Variable.Set random number("g", "1", "8")
     Variable.Get from collection("and", "{g}", "j")
     Function.Execute("{j}")
     Variable.Set random number("g", "1", "8")
     Variable.Get from collection("and", "{g}", "j")
     Function.Execute("{j}")
     Variable.Set random number("g", "1", "8")
     Variable.Get from collection("and", "{g}", "j")
     Function.Execute("{j}")
     Variable.Set random number("g", "1", "8")
     Variable.Get from collection("and", "{g}", "j")
     Function.Execute("{j}")
     Variable.Set random number("g", "1", "8")
     Variable.Get from collection("and", "{g}", "j")
     Function.Execute("{j}")
     Function.Execute("Attack")
     Function.Execute("Loot4")
     Function.Execute("AutoPots")
     Function.Execute("Restart")
     Function.Execute("Attack")
     Macro.Restart("no")
 end

function("Attack")
     begin
          // Teleport if Monster to avoid is found
          Function.Execute("EmergencyFlyWing")
          // Click Monster if Located
          if  Color.Can be located on screen (RGB)("255", "255", "0", "0")
               begin
                    Mouse.Release button("left")
                    Mouse.Click at color closest to coordinate (RGB)("255", "255", "0", "0", "645", "390", "left")
                    Variable.Add (Math)("at", "1")
                    Variable.Set("l", "0")
                    // Mouse.Move to coordinate("997 ", "43")
                    // Mouse.Move to coordinate("270", "40")
                    // Teleport if clicking on the monster a number of times but still the name isn't shown
                    if  Color.Pixel pattern can not be located on screen("255,198,198,0,-1,255,198,198,0,2,255,198,198", "4")
                         begin
                              Variable.Add (Math)("IsNotValidMonster", "1")
                              Macro.Pause("500")
                              if  Variable.Is greater than (Math)("IsNotValidMonster", "{HowManyAttackAttempt}")
                                   begin
                                        Variable.Set("IsNotValidMonster", "1")
                                        Function.Execute("FlyWithoutCondition")
                                   end
                         end
                    // If the monster isn't dead within the set number of seconds it will teleport
                    if  Color.Pixel pattern can be located on screen("255,198,198,0,-1,255,198,198,0,2,255,198,198", "4")
                         begin loop()
                              Variable.Add (Math)("at", "1")
                              Macro.Pause("500")
                              Macro.Get parent loop iteration("count")
                              Variable.Set("x", "{count}")
                              if  Variable.Is equal to("x","26")
                                   begin
                                        Function.Execute("Loot4")
                                        Function.Execute("FlyWithoutCondition")
                                   end
                              Macro.Pause("300")
                              Function.Execute("Loot4")
                              Function.Execute("IfNeedToPotion")
                              // Teleport if Monster to avoid is found
                              Function.Execute("Loot4")
                              Function.Execute("EmergencyFlyWing")
                              if  Color.Pixel pattern can not be located on screen("255,198,198,0,-1,255,198,198,0,2,255,198,198", "4")
                                   begin
                                        if  Variable.Is greater than (Math)("IsNotValidMonster", "{HowManyAttackAttempt}")
                                             or
                                             Variable.Is greater than (Math)("at", "30")
                                             begin
                                                  Variable.Set("IsNotValidMonster", "1")
                                                  Function.Execute("FlyWithoutCondition")
                                             end
                                        Variable.Set("IsNotValidMonster", "1")
                                        Macro.Pause("300")
                                        Function.Execute("Loot4")
                                        Function.Execute("Attack")
                                        Macro.Break from loop("yes")
                                        Variable.Set("at", "0")
                                   end
                         end
               end
     end
function

function("Loot4")
     begin
          if  Color.Can be located on screen (RGB)("0", "0", "255", "0")
               begin loop()
                    Mouse.Release button("left")
                    Mouse.Click at color closest to coordinate (RGB)("0", "0", "255", "0", "644", "392", "left")
                    Macro.Pause("100")
                    Variable.Add (Math)("l", "1")
                    if  Variable.Is greater than (Math)("l", "10")
                         begin
                              Mouse.Click at coordinate("733", "353", "left")
                              Variable.Set("l", "0")
                              if  Color.Can not be located on screen (RGB)("0", "0", "255", "0")
                                   begin
                                        Macro.Break from loop("yes")
                                   end
                         end
               end
     end
function

function("1")
     begin
          if  Color.Can not be located on screen (RGB)("255", "255", "0", "0")
               and
               Color.Can not be located on screen (RGB)("0", "0", "255", "0")
               and
               Variable.Is less than (Math)("a", "40")
               begin loop()
                    Mouse.Release button("left")
                    Variable.Add (Math)("a", "1")
                    Variable.Set("a1", "{a}")
                    Mouse.Click("left")
                    Mouse.Hold button("left")
                    Mouse.Move to coordinate("{mx}", "{my}")
                    while  Color.Can be located on screen (RGB)("255", "255", "0", "0")
                         or
                         Color.Can be located on screen (RGB)("0", "0", "255", "0")
                         begin
                              Mouse.Release button("left")
                              Variable.Set("j", " 1")
                              Function.Execute("Attack")
                              Function.Execute("Loot4")
                         end
                    if  Variable.Is greater than (Math)("a1", "39")
                         begin
                              Macro.Break from loop("yes")
                         end
                    if  Mouse.Is above color (RGB)("189", "189", "198")
                         or
                         Color.At the current mouse position is (RGB)("189", "189", "198")
                         or
                         Color.Near the current mouse position is (RGB)("189", "189", "198", "3")
                         or
                         Color.At coordinate is (RGB)("189", "189", "198", "{mx}", "{my}")
                         begin
                              Macro.Break from loop("yes")
                              Variable.Set("a1", "40")
                         end
               end
     end
function

function("2")
     begin
          if  Color.Can not be located on screen (RGB)("255", "255", "0", "0")
               and
               Color.Can not be located on screen (RGB)("0", "0", "255", "0")
               and
               Variable.Is less than (Math)("b", "40")
               begin loop()
                    Mouse.Release button("left")
                    Variable.Add (Math)("b", "1")
                    Variable.Set("b1", "{b}")
                    Mouse.Click("left")
                    Mouse.Hold button("left")
                    Mouse.Move to coordinate("{mx2}", "{my2}")
                    while  Color.Can be located on screen (RGB)("255", "255", "0", "0")
                         or
                         Color.Can be located on screen (RGB)("0", "0", "255", "0")
                         begin
                              Mouse.Release button("left")
                              Variable.Set("j", "2 ")
                              Function.Execute("Attack")
                              Function.Execute("Loot4")
                         end
                    if  Mouse.Is above color (RGB)("189", "189", "198")
                         or
                         Color.At the current mouse position is (RGB)("189", "189", "198")
                         or
                         Color.Near the current mouse position is (RGB)("189", "189", "198", "3")
                         or
                         Color.At coordinate is (RGB)("189", "189", "198", "{mx2}", "{my2}")
                         begin
                              Macro.Break from loop("yes")
                              Variable.Set("b1", "40")
                         end
                    if  Variable.Is greater than (Math)("b1", "39")
                         begin
                              Macro.Break from loop("yes")
                         end
               end
     end
function

function("3")
     begin
          if  Color.Can not be located on screen (RGB)("255", "255", "0", "0")
               and
               Color.Can not be located on screen (RGB)("0", "0", "255", "0")
               and
               Variable.Is less than (Math)("c", "40")
               begin loop()
                    Mouse.Release button("left")
                    Variable.Add (Math)("c", "1")
                    Variable.Set("c1", "{c}")
                    Mouse.Click("left")
                    Mouse.Hold button("left")
                    Mouse.Move to coordinate("{mx3}", "{my3}")
                    while  Color.Can be located on screen (RGB)("255", "255", "0", "0")
                         or
                         Color.Can be located on screen (RGB)("0", "0", "255", "0")
                         begin
                              Mouse.Release button("left")
                              Variable.Set("j", " 3")
                              Function.Execute("Attack")
                              Function.Execute("Loot4")
                         end
                    if  Mouse.Is above color (RGB)("140", "140", "140")
                         or
                         Color.At the current mouse position is (RGB)("140", "140", "140")
                         or
                         Color.Near the current mouse position is (RGB)("140", "140", "140", "3")
                         or
                         Color.At coordinate is (RGB)("140", "140", "140", "{mx3}", "{my3}")
                         begin
                              Macro.Break from loop("yes")
                              Variable.Set("c1", "40")
                         end
                    if  Variable.Is greater than (Math)("c1", "39")
                         begin
                              Macro.Break from loop("yes")
                         end
               end
     end
function

function("4")
     begin
          if  Color.Can not be located on screen (RGB)("255", "255", "0", "0")
               and
               Color.Can not be located on screen (RGB)("0", "0", "255", "0")
               and
               Variable.Is less than (Math)("d", "40")
               begin loop()
                    Mouse.Release button("left")
                    Variable.Add (Math)("d", "1")
                    Variable.Set("d1", "{d}")
                    Mouse.Click("left")
                    Mouse.Hold button("left")
                    Mouse.Move to coordinate("{mx4}", "{my4}")
                    while  Color.Can be located on screen (RGB)("255", "255", "0", "0")
                         or
                         Color.Can be located on screen (RGB)("0", "0", "255", "0")
                         begin
                              Mouse.Release button("left")
                              Variable.Set("j", " 4")
                              Function.Execute("Attack")
                              Function.Execute("Loot4")
                         end
                    if  Mouse.Is above color (RGB)("140", "140", "140")
                         or
                         Color.At the current mouse position is (RGB)("140", "140", "140")
                         or
                         Color.Near the current mouse position is (RGB)("140", "140", "140", "3")
                         or
                         Color.At coordinate is (RGB)("140", "140", "140", "{mx4}", "{my4}")
                         begin
                              Macro.Break from loop("yes")
                              Macro.Reset stopwatch("greywatch")
                              Variable.Set("d1", "40")
                         end
                    if  Variable.Is greater than (Math)("d1", "39")
                         begin
                              Macro.Break from loop("yes")
                         end
               end
     end
function

function("AutoPots")
     begin
          Macro.Execute new("RAGNAROK", "autopot", "yes")
     end
function

function("Restart")
     begin
          Variable.Set("a1", "{a}")
          Variable.Set("b1", "{b}")
          Variable.Set("c1", "{c}")
          Variable.Set("d1", "{d}")
          Variable.Set("e1", "{e}")
          Variable.Set("f1", "{f}")
          Variable.Set("h1", "{h}")
          Variable.Set("i1", "{i}")
          if  Variable.Is greater than (Math)("a1", "39")
               and
               Variable.Is greater than (Math)("b1", "39")
               and
               Variable.Is greater than (Math)("c1", "39")
               and
               Variable.Is greater than (Math)("d1", "39")
               and
               Variable.Is greater than (Math)("e1", "39")
               and
               Variable.Is greater than (Math)("f1", "39")
               and
               Variable.Is greater than (Math)("h1", "39")
               and
               Variable.Is greater than (Math)("i1", "39")
               begin
                    Macro.Restart("yes")
               end
          if  Variable.Is less than (Math)("a", "40")
               begin
                    Function.Execute("1")
               end
          if  Variable.Is less than (Math)("b", "40")
               begin
                    Function.Execute("2")
               end
          if  Variable.Is less than (Math)("c", "40")
               begin
                    Function.Execute("3")
               end
          if  Variable.Is less than (Math)("d", "40")
               begin
                    Function.Execute("4")
               end
          if  Variable.Is less than (Math)("e", "40")
               begin
                    Function.Execute("5")
               end
          if  Variable.Is less than (Math)("f", "40")
               begin
                    Function.Execute("6")
               end
          if  Variable.Is less than (Math)("h", "40")
               begin
                    Function.Execute("7")
               end
          if  Variable.Is less than (Math)("i", "40")
               begin
                    Function.Execute("8")
               end
     end
function
 
