# Final Installation Tips and Next Steps

When you are done with configuration, run the game to test out the integration. You should be able to control your character as normal and if you turn on Gizmos for the sensors and reward components, you should be able to see values for the sensors and the score achieved, as well as the objects being detected by the grid sensor. The game should also be initialized properly and should reset when the game is over. If anything is not working here, stop and revisit those settings again to debug and fix them.

Once your game works, you can test out the training process in the editor. Open the Realm AI menu and select "Train in Editor". This will open up the Python GUI to initialize training. The options within the Python GUI is explained in the [Python GUI documentation pages](../../python_gui/description){:target="_blank"}. When you choose "Train in Editor", a small editor window will open which will automatically run the game when the training starts.  

If the training seems to work in the editor, with no errors or bugs when you train for a while, you can perform the full training process with a build by opening the Realm AI menu and selecting "Make Build and Train". This will prompt you to make build, and then open up the Python GUI to initialize the full tuning and training process with the build that was just made. The "Train with Existing Build" option does the same thing, but instead of making a new build, you will be prompted to select an existing build to train with.

When the training is done, you can come back into this menu and select "Open Results Directory" to open the directory in the training results are stored. You can also then select "Open Dashboard" to open the dashboard web app to generate heatmaps and see the list of videos replays.





