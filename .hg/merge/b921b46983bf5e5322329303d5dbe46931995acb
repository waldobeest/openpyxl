from __future__ import absolute_import
# Copyright (c) 2010-2019 openpyxl

"""
Read a chart
"""

from .chartspace import ChartSpace, PlotArea
from openpyxl.xml.functions import fromstring

_types = ('areaChart', 'area3DChart', 'lineChart', 'line3DChart',
         'stockChart', 'radarChart', 'scatterChart', 'pieChart', 'pie3DChart',
         'doughnutChart', 'barChart', 'bar3DChart', 'ofPieChart', 'surfaceChart',
         'surface3DChart', 'bubbleChart',)

_axes = ('valAx', 'catAx', 'dateAx', 'serAx',)


def read_chart(chartspace):
    cs = chartspace
    plot = cs.chart.plotArea

    chart = plot._charts[0]
    chart._charts = plot._charts

    chart.title = cs.chart.title
    chart.display_blanks = cs.chart.dispBlanksAs
    chart.visible_cells_only = cs.chart.plotVisOnly
    chart.layout = plot.layout
    chart.legend = cs.chart.legend

    # 3d attributes
    chart.floor = cs.chart.floor
    chart.sideWall = cs.chart.sideWall
    chart.backWall = cs.chart.backWall
    chart.pivotSource = cs.pivotSource
    chart.pivotFormats = cs.chart.pivotFmts
    min_input = []
    for s in chart.series:
        min_input.append(s.idx)
    chart.idx_base = min(min_input) if min_input else 0

    return chart
