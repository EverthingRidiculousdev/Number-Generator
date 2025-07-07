# Number-Generator
You make use this software for anything you see fit 100% Unrestictided, except the POP.wav sound effect that I made, I will be using it again.
Here is the itch.io link: https://everything-ridiculous.itch.io/random-number-generator
Here is the full code in lua:







function love.load()
    love.window.setMode(0, 0, {fullscreen = true})
    love.graphics.setBackgroundColor(26/255, 121/255, 255/255)
    mainFont = love.graphics.newFont("LibertinusMono-Regular.ttf", 100)
    tutorialFont = love.graphics.newFont("LibertinusMono-Regular.ttf", 20) -- Smaller font for tutorial
    love.graphics.setFont(mainFont)
    num = 0
    tutorial = "Press space to generate a random number between 1 and 10. Press escape to exit fullscreen."
end

function love.keypressed(key)
    if key == "escape" and love.window.getFullscreen() then
        love.window.setFullscreen(false)
    elseif key == "space" then
        num = math.random(1, 10)
        love.audio.play(love.audio.newSource("POP.wav", "static"))
    end
end

function love.draw()

    love.graphics.setFont(mainFont)
    local text = tostring(num)
    local textWidth = mainFont:getWidth(text)
    local textHeight = mainFont:getHeight()
    local windowWidth = love.graphics.getWidth()
    local windowHeight = love.graphics.getHeight()
    local x = (windowWidth - textWidth) / 2
    local y = (windowHeight - textHeight) / 2
    love.graphics.print(text, x, y)

    love.graphics.setFont(tutorialFont)
    local tutorialText = tostring(tutorial)
    local tutorialWidth = tutorialFont:getWidth(tutorialText)
    local tutorialHeight = tutorialFont:getHeight()
    local tutorialX = (windowWidth - tutorialWidth) / 2
    local tutorialY = y - 300
    love.graphics.print(tutorialText, tutorialX, tutorialY)
end
function love.conf(t)
    t.window.highdpi = true
end
