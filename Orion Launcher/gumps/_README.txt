----------------------------------------------------------------------------

---=== Global variables ===---

Orion - Orion core object [Orion class];
Gump - current gump [Component class];
Model - current component model in gump [Component class];
Player - the player who entered the game [Character class].

----------------------------------------------------------------------------

---=== Text options ===---

Align can be:
'left'
'right'
'center'

Flags can be:
'solid' - bold text style
'italic' - italic text style
'indention' - text with indention in paragraph
'blackborder' - text with a black border
'underline' - underline text style
'fixed' - fixed text width by pixels
'cropped' - fixed text width by pixels with ... in the end of the text, if limit reached
'bq' - not sure about it :) seems like to indention and something else

Position can be:
'bottom'
'left'
'right'
'topcenter'
'bottomcenter'
'leftcenter'
'rightcenter'

----------------------------------------------------------------------------

---=== Orion class functions ===---

uint Orion.MakeProtocolVersion('version');
  version - string, client version, e.g: Orion.MakeProtocolVersion('2.0.3') or Orion.MakeProtocolVersion('5.0.0a') or Orion.MakeProtocolVersion('7.0.23.1') etc...
  return-value - number, numeric representation of client version.

uint Orion.ProtocolVersion();
  return-value - number, numeric representation of current protocol version.

string Orion.ClientVersion();
  return-value - string, current client version.

string Orion.OrionVersion();
  return-value - string, current Orion version.

Character Orion.FindNewTargetSystemTarget();
  return-value - Character class, new target system current object.

Character Orion.FindObject('serial');
  return-value - Character class, found game object.

bool Orion.OldStyleStatusbar();
  return-value - bool, old style statusbar option state.

----------------------------------------------------------------------------
---=== Component class functions ===---

// Setters (no-return value functions)
obj.SetSerial('serial');
  serial - string, text constant or numeric value of component serial number

obj.SetX(x);
  x - number, x-coordinate of the component

obj.SetY(y);
  y - number, y-coordinate of the component

obj.SetMinimizedX(minimizedX);
  minimizedX - number, x-coordinate of the gump in minimized state

obj.SetMinimizedY(minimizedY);
  minimizedY - number, y-coordinate of the gump in minimized state

obj.SetMinimized(state);
  state - bool, minimized state of the gump

obj.SetNoMove(state);
  state - bool, no move state of the gump

obj.SetNoClose(state);
  state - bool, no close state of the gump

obj.SetVisible(state);
  state - bool, visible state of the gump

obj.SetDrawOnly(state);
  state - bool, use this component for rendering only, no seection

obj.SetSelectOnly(state);
  state - bool, use this component for selection only, no rendering

obj.SetMoveOnDrag(state);
  state - bool, no block moving the gump when this compinent is pressed by mouse

//Only for CGUITextEntry start
obj.SetCheckOnSerial(state);
  state - bool, if this field is true - the OnTextEntry event is triggered if the user clicks on a component with the same serial number

obj.SetMask('mask');
  mask - string, visual mask for this textentry data (1 symbol)

obj.SetFocus();

obj.SetNumbersOnly(state);
  state - bool, this component accepts only numbers for input

obj.SetReadOnly(state);
  state - bool, this component is read only

obj.SetFocusedOffsetY(offset);
  offset - number, the y-coordinate offset for the text, if this component is selected
//Only for CGUITextEntry end

obj.SetLineWidth(width);
  width - number, line width in pixels

obj.SetUpdateWithoutOptimizations(state);
  state - bool, enable/disable rendering optimizations for statusbar gump



// Getters
uint obj.Serial();
  return-value - number, serial of this component.

int obj.X();
  return-value - number, x coordinate.

int obj.Y();
  return-value - number, y coordinate.

int obj.MinimizedX();
  return-value - number, x gump coordinate (if gump is minimized).

int obj.MinimizedY();
  return-value - number, y gump coordinate (if gump is minimized).

bool obj.Minimized();
  return-value - bool, minimized state of this gump.

bool obj.NoMove();
  return-value - bool, no move state of this gump.

bool obj.NoClose();
  return-value - bool, no close state of this gump.

bool obj.Visible();
  return-value - bool, visible state of this gump.

bool obj.DrawOnly();
  return-value - bool, rendering only state of this gump.

bool obj.SelectOnly();
  return-value - bool, select only state of this gump.

obj.SetMoveOnDrag(state);
  return-value - bool, no block moving state the gump when this compinent is pressed by mouse

//Only for CGUITextEntry start
bool obj.CheckOnSerial();
  return-value - bool, visible state of this gump.

String obj.Mask();
  return-value - string, text mask symbol.

bool obj.Focused();
  return-value - bool, focused state of this component.

bool obj.NumbersOnly();
  return-value - bool, numbers only textentry state of this component.

bool obj.ReadOnly();
  return-value - bool, read only textentry state of this component.

int obj.FocusedOffsetY();
  return-value - number, the y-coordinate offset for the text of this component.
//Only for CGUITextEntry end

int obj.LineWidth();
  return-value - number, line width in pixels of this component.

bool obj.SetUpdateWithoutOptimizations(state);
  return-value - bool, rendering optimizations state for statusbar gump



int obj.Type();
  return-value - number, component type.

bool obj.IsValid();
  return-value - bool, check is valid component.

bool obj.IsEmpty();
  return-value - bool, check is empty container object.

bool obj.IsGump();
  return-value - bool, check is gump component.

bool obj.IsPlayersGump();
  return-value - bool, check is player's gump component.

bool obj.UsePaperdollBooks();
  return-value - bool, use paperdoll books global variable value.

bool obj.DrawStatLockers();
  return-value - bool, draw stat lockers global variable value.

String obj.GetGoldText(value);
  value - number, gold amount.
  return-value - string, parsed to '123,456,789' gold value (dependent on option).

StringList GetGroupSerials();
  return-value - string list, statusbars group gump active serials

String GetCachedName('serial');
  serial - string, character serial.
  return-value - string, cached character name or 'out of range' if the character has never appeared on the screen



Component obj.FindControl('type', 'serial');
  type - string, component type.
  serial - string, component internal serial.
    default-value - '0'
  return-value - Component class, found Component class object on null.



// return-value for all "Add*" functions below is a created Component class object.
Component obj.AddPage(index);
  index - number, page index.

Component obj.AddGroup(index);
  index - number, group index.

Component obj.AddDataBox('serial');
  serial - string, component serial.
    default-value - '0'

Component obj.AddHitBox('serial', x, y, width, height, callOnMouseUp);
  serial - string, component serial.
  x - number, x coordinate.
  y - number, y coordinate.
  width - number, width.
  height - number, height.
  callOnMouseUp - bool, call event on mouse up (or on mouse down).
    default-value - false

Component obj.AddResizePic('serial', 'graphic', x, y, width, height);
  serial - string, component serial.
  graphic - string, component resizepic's graphic.
  x - number, x coordinate.
  y - number, y coordinate.
  width - number, width.
  height - number, height.

Component obj.AddCheckerTrans(x, y, width, height);
  x - number, x coordinate.
  y - number, y coordinate.
  width - number, width.
  height - number, height.

Component obj.AddScissor(state, baseX, baseY, x, y, width, height);
  state - bool, enabled or disabled.
  baseX - number, base x coordinate of component's container.
  baseY - number, base y coordinate of component's container.
  x - number, x coordinate.
  y - number, y coordinate.
  width - number, width.
  height - number, height.

Component obj.AddGumpPic('serial', 'graphic', 'color', x, y, width, height);
  serial - string, component serial.
  graphic - string, component graphic.
  color - string, component color.
  x - number, x coordinate.
  y - number, y coordinate.
  width - number, width.
    default-value - 0
  height - number, height.
    default-value - 0

Component obj.AddGumpPicHighlighted('serial', 'graphic', 'color', 'selectedColor', x, y, width, height);
  serial - string, component serial.
  graphic - string, component graphic.
  color - string, component color.
  selectedColor - string, component color when the component is hovered by mouse.
  x - number, x coordinate.
  y - number, y coordinate.
  width - number, width.
    default-value - 0
  height - number, height.
    default-value - 0

Component obj.AddButton('serial', 'graphic', 'graphicHovered', 'graphicPressed', x, y, 'color', toPage);
  serial - string, component serial.
  graphic - string, component graphic.
  graphicHovered - string, component graphic when the component is hovered by mouse.
  graphicPressed - string, component graphic when the component is pressed by mouse.
  x - number, x coordinate.
  y - number, y coordinate.
  color - string, component color.
    default-value - '0'
  toPage - number, page index to navigate in the gump.
    default-value - -100

Component obj.AddButtonTileArt('serial', 'graphic', 'graphicHovered', 'graphicPressed', x, y, 'color', toPage, 'tileGraphic', 'tileColor', tileX, tileY);
  serial - string, component serial.
  graphic - string, component graphic.
  graphicHovered - string, component graphic when the component is hovered by mouse.
  graphicPressed - string, component graphic when the component is pressed by mouse.
  x - number, x coordinate.
  y - number, y coordinate.
  color - string, component color.
  toPage - number, page index to navigate in the gump.
  tileGraphic - string, tile graphic.
  tileColor - string, tile color.
  tileX - number, tile x coordinate.
  tileY - number, tile y coordinate.

Component obj.AddResizeButton('serial', 'graphic', 'graphicHovered', 'graphicPressed', x, y, 'color');
  serial - string, component serial.
  graphic - string, component graphic.
  graphicHovered - string, component graphic when the component is hovered by mouse.
  graphicPressed - string, component graphic when the component is pressed by mouse.
  x - number, x coordinate.
  y - number, y coordinate.
  color - string, component color.
    default-value - '0'

Component obj.AddCheckBox('serial', 'graphic', 'graphicHovered', 'graphicChecked', 'graphicDisabled', x, y, state, 'color');
  serial - string, component serial.
  graphic - string, component graphic.
  graphicHovered - string, component graphic when the component is hovered by mouse.
  graphicChecked - string, component graphic when the component is checked.
  graphicDisabled - string, component graphic when the component is disabled.
  x - number, x coordinate.
  y - number, y coordinate.
  state - bool, checked/unchecked state.
  color - string, component color.
    default-value - '0'

Component obj.AddRadioButton('serial', 'graphic', 'graphicHovered', 'graphicChecked', 'graphicDisabled', x, y, state, 'color');
  serial - string, component serial.
  graphic - string, component graphic.
  graphicHovered - string, component graphic when the component is hovered by mouse.
  graphicChecked - string, component graphic when the component is checked.
  graphicDisabled - string, component graphic when the component is disabled.
  x - number, x coordinate.
  y - number, y coordinate.
  state - bool, checked/unchecked state.
  color - string, component color.
    default-value - '0'

Component obj.AddTilePic('serial', 'graphic', x, y, 'color', 'colorHovered', doubleDraw);
  serial - string, component serial.
  graphic - string, component graphic.
  x - number, x coordinate.
  y - number, y coordinate.
  color - string, component color.
    default-value - '0'
  colorHovered - string, component color when the component is hovered by mouse.
    default-value - '0'
  state - bool, draw stacked or single item.
    default-value - false

Component obj.AddScrolledArea('serial, 'graphic', x, y, width, height, haveBackground, haveScrollbar);
  serial - string, component serial.
  graphic - string, component graphic.
  x - number, x coordinate.
  y - number, y coordinate.
  width - number, area width.
  height - number, area height.
  state - bool, draw background.
    default-value - true
  state - bool, draw scroll bar.
    default-value - true

Component obj.AddText('serial', x, y, 'text', clilocID, unicode, font, 'color', maxWidth, 'align', 'flags');
  serial - string, component serial.
  x - number, x coordinate.
  y - number, y coordinate.
  text - string, text data to render.
  clilocID - number, clicoc ID, if needed (text will be replaced to data from clilocs).
    default-value - 0
  unicode - bool, unicode or ASCII text style.
    default-value - true
  font - number, font number.
    default-value - 0
  color - string, text color.
    default-value - '0'
  maxWidth - number, maximum text width in pixels (if needed).
    default-value - 0
  align - string, text alignment.
    default-value - 'left'
  flags - string, text flags.
    default-value - ''

Component obj.AddTextEntry('serial', x, y, 'text', unicode, font, 'color', 'colorHovered', 'colorFocused', maxWidth, 'align', 'flags', maxLength);
  serial - string, component serial.
  x - number, x coordinate.
  y - number, y coordinate.
  text - string, text data to render.
  unicode - bool, unicode or ASCII text style.
    default-value - true
  font - number, font number.
    default-value - 0
  color - string, text color.
    default-value - '0'
  colorHovered - string, text color when the component is hovered by mouse.
    default-value - '0'
  colorFocused - string, text color when caret in this component at now.
    default-value - '0'
  maxWidth - number, maximum text width in pixels (if needed).
    default-value - 0
  align - string, text alignment.
    default-value - 'left'
  flags - string, text flags.
    default-value - ''
  maxLength - number, maximum text length in symbols (if needed).
    default-value - 0

Component obj.AddSlider('serial', 'graphic', 'graphicHovered', 'graphicPressed', 'backgroundGraphic', x, y, compositeBackground, vertical, length, minValue, maxValue, value);
  serial - string, component serial.
  graphic - string, component graphic.
  graphicHovered - string, component graphic when the component is hovered by mouse.
  graphicPressed - string, component graphic when the component is pressed by mouse.
  backgroundGraphic - string, component background graphic.
  x - number, x coordinate.
  y - number, y coordinate.
  compositeBackground - bool, composite background from three gumps or resizepic.
  vertical - bool, vertical or horisontal alighment.
  length - number, length in pixels.
  minValue - number, minimal value.
  maxValue - number, maximal value.
  value - number, default value.

Component obj.AddLine('serial', startX, startY, endX, endY, argb);
  serial - string, component serial.
  startX - number, start x coordinate.
  startY - number, start y coordinate.
  endX - number, end x coordinate.
  endY - number, end y coordinate.
  argb - number, line color.

Component obj.AddPolygone('serial', 'reservedColor', x, y, int width, int height, argb, scopeOnly, lineWidth);
  serial - string, component serial.
  reservedColor - string, unused argument.
  x - number, x coordinate.
  y - number, y coordinate.
  width - number, polygone width.
  height - number, polygone  height.
  argb - number, polygone color.
    default-value - 0
  scopeOnly - bool, draw filled polygone or scope only.
    default-value - false
  lineWidth - number, scope lines width in pixels.
    default-value - 1



void obj.SetTooltip(clilocID, 'defaultText', maxWidth, toCamelCase);
  clilocID - number, tooltip clicoc ID, if needed (text will be replaced to data from clilocs).
  defaultText - string, component tooltip text.
  maxWidth - number, tooltip area width in pixels.
    default-value - 0
  toCamelCase - bool, transform text to Upper Camel Case.
    default-value - false

//Only for CGUICheckbox/CGUIRadio start

void obj.SetTextLabel(clilocID, 'text', 'position', unicode, font, 'color', maxWidth, 'align', 'flags');
  clilocID - number, clicoc ID, if needed (text will be replaced to data from clilocs).
  text - string, component text.
  position - string, component text position.
    default-value - 'right'
  unicode - bool, unicode or ASCII text style.
    default-value - true
  font - number, font number.
    default-value - 0 for unicode and 9 for ASCII
  color - string, text color.
    default-value - '0'for unicode and '0x0386' for ASCII
  maxWidth - number, maximum text width in pixels (if needed).
    default-value - 0
  align - string, text alignment.
    default-value - 'left'
  flags - string, text flags.
    default-value - ''

//Only for CGUICheckbox/CGUIRadio end

//Only for CGUISlider start

void obj.SetTextConfig('position', unicode, font, 'color', maxWidth, 'align', 'flags');
  position - string, component text position.
    default-value - 'right'
  unicode - bool, unicode or ASCII text style.
    default-value - true
  font - number, font number.
    default-value - 0 for unicode and 9 for ASCII
  color - string, text color.
    default-value - '0'for unicode and '0x0386' for ASCII
  maxWidth - number, maximum text width in pixels (if needed).
    default-value - 0
  align - string, text alignment.
    default-value - 'left'
  flags - string, text flags.
    default-value - ''

//Only for CGUISlider end

----------------------------------------------------------------------------

---=== Character class functions ===---

bool obj.IsValid();

QString obj.ColorByNotoriety();

bool obj.OutOfRange();

bool obj.Frozen();

bool obj.Poisoned();

bool obj.Flying();

bool obj.YellowHits();

bool obj.IgnoreCharacters();

bool obj.Locked();

bool obj.InWarMode();
  return-value - bool, current war mode state.

bool obj.Hidden();

bool obj.IsHuman();

bool obj.CanChangeName();

int obj.Notoriety();

int obj.Hits();

int obj.MaxHits();

int obj.Mana();

int obj.MaxMana();

int obj.Stam();

int obj.MaxStam();

QString obj.Name();

bool obj.Female();

QString obj.Sex();

int obj.Str();

int obj.Int();

int obj.Dex();

int obj.LockStr();

int obj.LockInt();

int obj.LockDex();

int obj.Weight();

int obj.MaxWeight();

int obj.Armor();

int obj.Gold();

int obj.StatsCap();

int obj.Followers();

int obj.MaxFollowers();

int obj.FireResistance();

int obj.ColdResistance();

int obj.PoisonResistance();

int obj.EnergyResistance();

int obj.MaxPhysicalResistance();

int obj.MaxFireResistance();

int obj.MaxColdResistance();

int obj.MaxPoisonResistance();

int obj.MaxEnergyResistance();

int obj.Luck();

int obj.MinDamage();

int obj.MaxDamage();

int obj.TithingPoints();

int obj.DefenceChance();

int obj.MaxDefenceChance();

int obj.AttackChance();

int obj.WeaponSpeed();

int obj.WeaponDamage();

int obj.LowerReagentCost();

int obj.SpellDamage();

int obj.CastRecovery();

int obj.CastSpeed();

int obj.LowerManaCost();

----------------------------------------------------------------------------
