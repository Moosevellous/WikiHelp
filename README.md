# Duct Breakout
`Function GetDuctBreakout(freq As String, H As Single, w As Single, L As Single, MaterialDensity As Single, DuctWallThickness As Single)`

This function is based on phenomenon wherein there is transmission of sound energy from the interior of the duct out through its walls and
into an occupied space or known as breakout. The procedure combines duct attenuation as well as the transmission loss through the duct
walls.

#### Figure 1. Duct Breakout Geometry

<img src="https://github.com/ianmichaelvillanueva/WikiHelp/blob/master/Breakout%20concept.png" width = 600>

For rectangular ducts, the transmission loss for breakout is divided into regions by frequency: a region where plane mode transmission
within the duct is dominant; and a region where multimode transmission is dominant as shown in Figure 2.

#### Figure 2. Transmission Loss for Rectangular Ducts

<img src="https://github.com/ianmichaelvillanueva/WikiHelp/blob/master/Breakout%20Graph.png" width = 500>

If plane mode predominates, TLout is:

`TLout = 10 * Application.WorksheetFunction.Log10((f * (SurfaceMass ^ 2)) / (w + H)) + 17`

While in multi-mode, TLout is:

`TLout = 20 * Application.WorksheetFunction.Log10(f * SurfaceMass) – 45`

However, in no case that the TLout be greater than 45 dB:

`If TLout > 45 Then TLout = 45`

In addition, when the fundamental wall resonance is below the frequency range of interest or the minimum transmission loss is dependent on
duct dimensions, minimum TLout is:

`TLoutMin = 10 * Application.WorksheetFunction.Log10(2 * L * 1000 * ((1 / w) + (1 / H)))`



# Duct Break-in

`Function GetDuctBreakIn(freq As String, H As Single, w As Single, L As Single, MaterialDensity As Single, DuctWallThickness As Single)`

Break-in is a phenomenon that covers the transmission of sound energy into a duct through the duct walls from the space outside the duct.

#### Figure 1. Duct Break-in Geometry

<img src="https://github.com/ianmichaelvillanueva/WikiHelp/blob/master/Breakin%20concept.png" width = 600>

The breakin transmission loss is divided in two regions separated by the frequency for the lowest acoustic cross-mode in the duct or the cutoff frequency.

If the frequency ≤ cutoff frequency, TLin is the larger value of the following equation:

`TLin_a = TLout - 4 - (10 * Application.WorksheetFunction.Log(a / b)) + (20 * Application.WorksheetFunction.Log(f / f1))`

`TLin_b = 10 * Application.WorksheetFunction.Log((L * 1000) * ((1 / a) + (1 / b)))`

In case, the frequency > cutoff frequency, TLin is:

`TLin1 = TLout - 3`

The sound power being transmitted from the exterior of the duct will depend on the type of sound field present in the space.

