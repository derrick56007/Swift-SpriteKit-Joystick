Joystick -TheSneakyNarwhal
====================
![alt tag](https://raw.githubusercontent.com/TheSneakyNarwhal/SpriteKit-Joystick/master/pic.png)
====================
How to make the joystick
=====================

1.Declare the Joystick variable --> var joystick: Joystick

2.Initialize it --> Joystick(thumbNode, backDrop). There are default images, --> Joystick()

3.Position The sprite (preferably --> CGPointMake(joystick.size.width/2, joystick.size.height/2)).

4.Add the child to the scene

    joystick = Joystick()
    joystick.zPosition = 3.0
    joystick.position = CGPointMake(joystick.backdropNode.size.width / 2, joystick.backdropNode.size.height / 2)
    joystick.shouldFadeOut = true
    self.addChild(joystick)

Movement
========

To use the joystick, use the velocity property --> joystick.velocity

For movement, you could do


    override func update(currentTime: CFTimeInterval) {
        if joystick.velocity.x != 0 || joystick.velocity.y != 0 {
              player.position = CGPointMake(player.position.x + 0.1 * joystick.velocity.x, player.position.y + 0.1 * joystick.velocity.y)
        }
    }

For animations

    if joystick.velocity.x > 0 {
        player.walkRightAnim()
    } else if joystick.x < 0 {
        player.walkLeftAnim()
    } if joystick.velocity.y > 0 {
        player.walkUpAnim()
    } else if joystick.velocity.y < 0 {
        player.walkDownAnim()
    } if joystick.velocity.x == 0 && joystick.velocity.y == 0 {
        player.idleAnim()
    }

                                                        
Rotation
========

For rotation, use the joystick property angularVelocity (joystick.angularVelocity)

    if joystick.velocity.x != 0 || joystick.velocity.y != 0
    {
        player.zRotation = joystick.angularVelocity
    }
    
PS: The formula for finding the radians of a point and the origin is -atan2(position.x - origin.x, position.y - origin.y)

If you want to find the angle in degrees, multiply the above formula by 180/M_PI

                                                        TheSneakyNarwhal
