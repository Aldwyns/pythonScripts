'''
testRender v1.4
Author Jon Murray Vinther
Contact jon@jonv.dk, www.jonv.dk
Last update 15-05-15
---------------------------------------
Description:
Changes some Maya render settings, and starts a render.
Created for Maya 2015.
Current Version:
Now renames files after render finish.
Does not change pixel size of output.
Forces use of specific camera.
---------------------------------------
This is free software:
You are free to redistribute it and/or modify it under the terms of the
Creative Commons Attribution-ShareAlike 4.0 International License.
To view a copy of this license, visit:
http://creativecommons.org/licenses/by-sa/4.0/
---------------------------------------
TODO:
Change shown location in UI after browsing.
Probably needs to use cmds.window in stead of layoutDialog to do so.

Have script go back to old render settings after render.

Fix white pixels from intersections (hwRender Problem)
Change to Hardware Render 2.0 (ogsRender does not support render layers though)
'''

import maya.cmds as cmds
import os


class testRender():
	def __init__(self):
		# Hardcoded path for render outputs
		self.outPath = 'E:/Testrender/'
		self.camera = 'persp'
		# Object filter for render. Contains to "print cmds.getAttr('hardwareRenderingGlobals.objectTypeFilterNameArray')"
		# Currently (NURBS Surfaces, Polygons)
		self.objValue = [0, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
		# Changing variable for whether or not to render only selected objects
		self.selRender = False

	def startUI(self):
		'''Start call for the script'''
		# Start UI
		cmds.layoutDialog(ui=self.dialogUI, title='Test Render')

	def dialogUI(self):
		'''Defines the UI for cmds.layoutDialog'''
		print 'Initialising Test Render UI!'
		# Get name of scene
		self.renderPath()
		# Define seize of window
		form = cmds.setParent(q=True)
		cmds.formLayout(form, edit=True, width=370, height=100)
		# Buttons and content
		message = cmds.text('This will change your render settings!\nStandard render location is:')
		# Editabe text field, does not work with layoutDialog - path = cmds.textField(width=300, height=25, text=self.renderFolder, enable=True)
		path = cmds.text(self.renderFolder)
		button1 = cmds.button('OK', c=self.startRender, width=50)
		button2 = cmds.button('Cancel', c='cmds.layoutDialog(dismiss="Test Render aborted.")', width=50)
		button3 = cmds.button('Browse', c=self.browse, width=50)
		cb1 = cmds.checkBox('Only render selection', onc=self.selRenOn, ofc=self.selRenOff)
		#button4 = cmds.button('Load cameras', c='print "load cameras"', width=100)
		# Define distances between buttons in dialog (some are currently typed directly in layout code)
		spacer = 5
		top = 5
		edge = 5
		# Placement of buttons and text in dialog window
		### With button4
		#cmds.formLayout(form, edit=True, attachForm=[(message, 'top', top), (message, 'left', edge), (message, 'right', edge), (button2, 'right', edge), (button1, 'bottom', edge), (button2, 'bottom', edge), (button3, 'left', edge), (button4, 'bottom', edge), (cb1, 'left', edge), (cb1, 'bottom', 8)], attachControl=[(button3, 'bottom', 12, cb1), (button1, 'right', spacer, button2), (path, 'left', 15, button3), (path, 'bottom', 17, cb1), (button4, 'right', spacer, button1)])
		### If button4 is disabled
		cmds.formLayout(form, edit=True, attachForm=[(message, 'top', top), (message, 'left', edge), (message, 'right', edge), (button2, 'right', edge), (button1, 'bottom', edge), (button2, 'bottom', edge), (button3, 'left', edge), (cb1, 'left', edge), (cb1, 'bottom', 8)], attachControl=[(button3, 'bottom', 12, cb1), (button1, 'right', spacer, button2), (path, 'left', 15, button3), (path, 'bottom', 17, cb1)])

	def browse(self, *args):
		'''Browse window for picking render output folder'''
		# Create browse dialog
		self.newPath = cmds.fileDialog2(fileMode=3, dialogStyle=1, dir=self.outPath)
		# Changes double backslash to single forward slash
		self.newPath = self.newPath and os.path.normpath(self.newPath[0]).replace('\\', '/')
		self.newPath.encode('ascii', 'ignore')
		# Change standard path to newly chosen one
		self.outPath = str(self.newPath) + '/'
		# Update renderPath
		self.renderPath()
		print 'Render path has been changed to: ' + self.renderFolder

	def checkSelection(self):
		'''Checks to see if you have a selected object'''
		mySelect = cmds.ls(selection=True)
		if not mySelect:
			return False
		else:
			return True

	def renderPath(self):
		'''Get and set output folder from scenename'''
		# Call getFileName to get variables
		self.getFileName()
		renderPath = self.renderFolder + self.sceneName + '_#' + '_%l'
		return renderPath

	def selRenOn(self, *args):
		'''Changes render selection variable to ON'''
		self.selRender = True
		print self.selRender

	def selRenOff(self, *args):
		'''Changes render selection variable to OFF'''
		self.selRender = False
		print self.selRender

	def startRender(self, *args):
		'''Start render'''
		# Change render settings
		print 'Changing render settings!!!'
		self.setSettings()
		print 'Will output render to: ' + self.renderFolder
		# Check if render selection has been enabled
		if self.selRender == 1:
			print 'Only rendering selection'
			# Dismiss UI
			cmds.layoutDialog(dismiss="Starting render!")
			# Start Render
			cmds.hwRender(noRenderView=True, renderSelected=True)
		else:
			# Dismiss UI
			cmds.layoutDialog(dismiss="Starting render!")
			# Start Render
			cmds.hwRender(noRenderView=True)
			#cmds.ogsRender(camera=self.camera, noRenderView=True)

	def setSettings(self):
		'''Settings to change before rendering'''
		# Set render
		cmds.setAttr('defaultRenderGlobals.ren', 'mayaHardware', type='string')
		# Set postrender scripts
		cmds.setAttr('defaultRenderGlobals.postRenderMel', 'python("import testRender;reload(testRender);testRender.testRender().postSettings()")', type='string')
		#### Post render scripts don't seem to start when calling hwRender - only post frame scripts
		#cmds.setAttr('defaultRenderGlobals.postMel', 'python("import testRender;reload(testRender);testRender.testRender()postSettings()")', type='string')
		# ImageFormat 8 is JPEG
		cmds.setAttr('defaultRenderGlobals.imageFormat', 8)
		cmds.setAttr('defaultRenderGlobals.outFormatControl', 0)
		# Set correct frame extensions
		cmds.setAttr('defaultRenderGlobals.animation', 1)
		cmds.setAttr('defaultRenderGlobals.putFrameBeforeExt', 1)
		cmds.setAttr('defaultRenderGlobals.extensionPadding', 4)
		# Set render range
		cmds.setAttr('defaultRenderGlobals.byFrame', 1)
		cmds.setAttr('defaultRenderGlobals.byFrameStep', 1)
		cmds.setAttr('defaultRenderGlobals.startFrame', cmds.playbackOptions(q=True, min=True))
		cmds.setAttr('defaultRenderGlobals.endFrame', cmds.playbackOptions(q=True, max=True))
		# Calls renderPath() to get output name and path
		cmds.setAttr('defaultRenderGlobals.imageFilePrefix', self.renderPath(), type='string')
		cmds.setAttr('defaultRenderGlobals.periodInExt', 1)
		cmds.setAttr('defaultRenderGlobals.useMayaFileName', 0)
		# Quiality settings on second tab
		cmds.setAttr('hardwareRenderingGlobals.ssaoEnable', 1)
		cmds.setAttr('hardwareRenderingGlobals.msaa', 1)
		cmds.setAttr('hardwareRenderingGlobals.gammaCorrectionEnable', 1)
		cmds.setAttr('hardwareRenderingGlobals.gammaValue', 1.2)
		cmds.setAttr('hardwareRenderingGlobals.batchRenderControls.lightingMode', 3)
		cmds.setAttr('hardwareRenderingGlobals.batchRenderControls.renderMode', 1)
		# Object Type Filter settings (NURBS Surfaces, Polygons)
		cmds.setAttr('hardwareRenderingGlobals.batchRenderControls.objectTypeFilterValueArray', self.objValue, type='Int32Array')
		# Set culling to Single Sided, to avoid white pixels from Harware Render
		cmds.setAttr('hardwareRenderGlobals.clmt', 2)

	def getFileName(self):
		# Get name of scene file, untitled if not saved
		self.sceneFile = cmds.file(q=True, sceneName=True, shortName=True)
		if len(self.sceneFile) == 0:
			self.sceneFile = 'untitled'
		# Seperate name from extension
		self.sceneName, sep, ext = self.sceneFile.partition('.')
		self.renderFolder = self.outPath + self.sceneName + '/'
		# Find current frame and file output name
		imgName = cmds.renderSettings(fin=True, fp=True)[0]
		curFrame = cmds.currentTime(q=True)
		curPadding = imgName.split('.')[1]
		self.newFile = imgName.replace(curPadding, '%04d' % int(curFrame))
		# Create new name from old
		self.newName = self.newFile.partition("_")[0] + '_' + '%04d' % int(curFrame) + "." + self.newFile.rpartition(".")[2]

	def pdComp(self):
		'''Create a pdPlayer composition and open it'''
		# Call getFileName to get variables
		self.getFileName()
		# Check if current frame file exists
		if os.path.isfile(self.newName):
			# Create text for file
			pdFile = self.newName.rpartition(".")[0] + '.pdpcmd'
			pdText = self.newName.partition("_")[0] + '_' + '####' + "." + self.newName.rpartition(".")[2]
			# Create file, overwrite it if already exists
			print 'Creating pdPlayer file: ' + pdText
			with open(pdFile, 'w') as pd:
				pd.write(pdText)
			# Open the comp in pdPlayer
			import webbrowser
			webbrowser.open(pdFile)
			del webbrowser

	def imgRename(self):
		'''Post frame script. Renames current render frame output to desired format'''
		# Run file name function to get variables
		self.getFileName()
		# Rename if no _temp
		if os.path.isfile(self.newFile):
			cmds.sysFile(self.newFile, rename=self.newName)
			print 'Renaming to: ' + self.newName
		# Rename if _temp
		tempName = self.newFile.rpartition(".")[0] + "_tmp." + self.newFile.rpartition(".")[2]
		print tempName
		if os.path.isfile(tempName):
			cmds.sysFile(tempName, rename=self.newName)
			print 'Renaming Temp name to: ' + self.newName

	def postSettings(self):
		'''Post render script. Undoes settings changed during script runtime- WIP'''
		# Run imgRename to change name of latest rendered file
		self.imgRename()
		# Check if frame was last to be rendered
		if cmds.currentTime(q=True) == cmds.getAttr('defaultRenderGlobals.endFrame'):
			print 'Works'
			cmds.setAttr('defaultRenderGlobals.postRenderMel', '', type='string')
			self.pdComp()
